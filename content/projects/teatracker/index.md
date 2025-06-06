---
title: Tea Purchase Statistics
date: 2025-03-30
categories: 
  - Project
  - Groupwork
  - Active
tags:
  - Data Science
  - Front-end
  - Back-end
  - Ruby
  - PostgreSQL
draft: false
---
This started, as all problems do, with me making facetious claims without proof on the Internet. 

> **User A** 
> Where did you feel that there were diminishing returns for tea? I've heard it's at around 1$ per gram
> 
> **skylarke** 
> think somewhere around $1.20-$1.50 it has started feeling iffier for me

About 10 seconds after posting that, I realized that I couldn't actually back it up, and that really bothered me. 
Someone could ask me 'Why?' and all I would be able to say was 'It feels like it', which is terrible for credibility. 
I like winning arguments and I hate being wrong, so I left the conversation to go find out the truth
(specifically in a way that involved data and could be easily shown to others). 

120 teas participated. I've taken the info from my personal notes over the past year and a half which 
include tea category, subtype, region, price, and more. 
The majority of the teas I drink are oolongs, followed by puer. 
Prices range from $0.11-$2.50/g, although ~75% are below $0.5/g. 
This doesn't take into account how frequently I drink each tea either, if I drink 100g of Dayi 7542 and twenty 
8g oolong samples, the 7542 will only show up once.

I have some data on Notion about prices and vendors, so I took that to a google sheets table. 
I used [monkeysort](https://leonid-shevtsov.github.io/monkeysort/) to order them, which is a website that when given a list, shows you two options at a time. 
You choose the winner between them. There are no ties, no rock-paper-scissors scenarios, 
no elements of nuance, just straight up A or B. I went off of the question of 
"If I had A or B, which one would I drink?". It was very vibes-based and I might 
have different answers tomorrow for the same teas. I reviewed the ranking after and moved
some that I felt weren't accurate, but there's enough data that I feel that I didn't need 
to split hairs and ranks could just be close enough. This does mean that the metric is 
continuous and evenly distributed, which isn't the case in reality. There's a large
delineation between 'top 5 teas ever!!' and 'mid'. (Some people use tier lists, but due to a 
different online community I'm involved with, I'm mildly allergic to them due to the feeling
that often there's little-to-no internal consistency about the criteria for each tier. If there's
multiple criteria, why not just rank them based on the criteria? Why do the tiers need to be involved?)

I measured cost efficiency using a metric that I will be referring to as "cost-rank score", 
which I calculated by adding each item's cost Z-score (# of standard deviations from the average) 
and its numerical rank's Z-score. I used Z-score so the average would be 0 and teas would be 
evenly distributed for my overall score. Cost was measured in $USD/g, and I used the 
non-discounted cost of the tea. If I couldn't find the exact listing, I found the closest 
possible one, or I removed it from the data. Teas were ranked from 1-120, 1 being the best, 
120 being the worst. After I added these values, I got each tea's Z-score for cost + rank, 
which I used as my final value.

I had some basic outlier checks. If the Z-score's absolute value was greater than 3, I dropped it. Still caused some outliers.

Some hypotheses I had:
- $1.2/g-$1.5/g is when diminishing returns begin (when it becomes less cost-efficient)
- ~$0.5/g is the most efficient price point for me
- Oolongs are the most price-efficient for me to buy


<h2 class="h2">Initial Results</h2>
First, I began with a Google Sheets demo. These charts are generated from there. Here is the 
[link](https://docs.google.com/spreadsheets/d/1yZQ4RzxCBcF8WIU29-2kzYp-AzNq7K2YjRN2l3hfOj0/).
<h3 class="h3">Overall</h3>
<div class="flex flex-col sm:flex-row flex-wrap items-center gap-2">
  <img src="rank-v-cost.svg" alt="graph of rank vs. cost" class="w-[1/2] h-auto">
  <img src="rank-v-price-eff.svg" alt="graph of rank vs. price efficiency" class="w-[1/2] h-auto">
  <img src="cost-v-price-eff.svg" alt="graph of cost vs. price efficiency" class="w-[1/2] h-auto">
</div>


<h3 class="h3">Oolong</h3>
<div class="flex flex-col sm:flex-row flex-wrap items-center gap-2">
<img src="oolong-rank-v-cost.svg" alt="graph of rank vs. cost" class="basis-1/3 h-auto">
<img src="oolong-rank-v-price-eff.svg" alt="graph of rank vs. price efficiency" class="basis-1/3 h-auto">
<img src="oolong-cost-v-price-eff.svg" alt="graph of cost vs. price efficiency" class="basis-1/3 h-auto">
</div>

<h3 class="h3">Puer</h3>
<div class="flex flex-col sm:flex-row flex-wrap items-center gap-2">
  <img src="puer-rank-v-cost.svg" alt="graph of rank vs. cost" class="basis-1/3 h-auto">
<img src="puer-rank-v-price-eff.svg" alt="graph of rank vs. price efficiency" class="basis-1/3 h-auto">
<img src="puer-cost-v-price-eff.svg" alt="graph of cost vs. price efficiency" class="basis-1/3 h-auto">
</div>

<h3 class="h3">White</h3>
<div class="flex flex-col sm:flex-row flex-wrap items-center gap-2">
  <img src="white-rank-v-cost.svg" alt="graph of rank vs. cost" class="basis-1/3 h-auto">
<img src="white-rank-v-price-eff.svg" alt="graph of rank vs. price efficiency" class="basis-1/3 h-auto">
<img src="white-cost-v-price-eff.svg" alt="graph of cost vs. price efficiency" class="basis-1/3 h-auto">
</div>

<h3 class="h3">Green</h3>
<div class="flex flex-col sm:flex-row flex-wrap items-center gap-2">
  <img src="green-rank-v-cost.svg" alt="graph of rank vs. cost" class="basis-1/3 h-auto">
<img src="green-rank-v-price-eff.svg" alt="graph of rank vs. price efficiency" class="basis-1/3 h-auto">
<img src="green-cost-v-price-eff.svg" alt="graph of cost vs. price efficiency" class="basis-1/3 h-auto">
</div>

<h3 class="h3">Black</h3>
<div class="flex flex-col sm:flex-row flex-wrap items-center gap-2">
  <img src="black-rank-v-cost.svg" alt="graph of rank vs. cost" class="basis-1/3 h-auto">
<img src="black-rank-v-price-eff.svg" alt="graph of rank vs. price efficiency" class="basis-1/3 h-auto">
<img src="black-cost-v-price-eff.svg" alt="graph of cost vs. price efficiency" class="basis-1/3 h-auto">
</div>

<h2 class="h2">Initial Conclusions</h2>
It was pointed out most of these lines are overfit and have lots of outliers, and I agree.
This would be a very poor classifier, since it quite literally is only checking if price & 
rank (subjective enjoyment) are correlated. Also, the discrete ranking system I did here is 
rather flawed - in reality there can be ties, large gaps, etc. I simply did not see a good
way of quantifying that, so I simplified it to the greatest extent. 

Perhaps I'm going in the wrong direction for this entirely. I want to figure out if a 
certain trait of a tea (price, type) correlates with my own subjective enjoyment. 

This seems more of a classic regression problem, and it seems the data is set up perfectly for supervised learning.
Also, it appears quite a few people have literal years worth of tea, wouldn't it be helpful to predict
the chance of liking a tea based upon previous experiences? 

<h2 class="h2">Web App Planning</h2>
Since I have the repetitive task tolerance of a 6-year-old after five Monsters and a basket of Halloween candy, 
I was absolutely fed up with Google Sheets after getting this far. Formatting data manually was bad enough, 
making a classifier on there would be even more of a test of my patience.

<!-- Naturally, the only way forward would be a webapp that trains a regression model upon your own tea data
and tells you what factors most affect your own personal enjoyment, complete with aesthetically appealing graphics
and summaries. Some may say that you could simply 'employ critical thinking', but does critical thinking have 
automation in it? -->

There will be more to this writeup - I just got caught up in actually making the app. 


<!-- <h2 class="h2">Database Decisions</h2>
So, I have to have a database for my webapp, and I'd want some way of uploading my data.

There are two tables I would need
1. User-submitted data (training data)
2. Table with extra information with 

Notion, where the original data is from is based on PostgreSQL, so I thought that was a good starting point. 
I did consider NoSQL, but the data is highly structured, so no point. Postgres should be good enough, and lets 
me use JSONs. I considered using a cloud provider such as AWSLambda or Supabase, but I'd like to keep this
self contained so people can fork and deploy their own versions. 
Okay, so I know I'm going to have my data in here, but how do I want to store it? What am I planning on doing with it?

The fields of the database would vary depending on the format. 
There are some known templates such as the one by Priestess, and there also is the MyTeaPal app, which allows for an export. 

Just to have a starting point, here are the fields in my personal spreadsheet:
* Tea name
* Cost per gram of tea (USD$/g)
* Vendor
* Type (e.g. black, green...)
    * Subtype (e.g. young sheng, dancong, although there is some debate about some categories, 
especially about what counts as 'aged', young, etc)
* Cultivar (e.g. )
* Country
* Rank

Most of the info is easily obtained from my personal notes, and the current spreadsheet. But rank is harder. 
I want to easily be able to rank a tea and shift all values accordingly as efficiently as possible.

As usual the solution is a hashmap.

Put all teas from database into a hashmap with their name as key. 
Then, iterate through all csv entries
If the entry is in the hashmap (already exists), then:
If the entry's values are all the same as the csv, continue
If the entry's values/rank are different, update it
Remove the entry from the hashmap. 

If the entry is not in the hashmap, add it with the current rank.

After everything is done, anything left in the hashmap is a deleted/edited/duped entry and should be removed. 

This goes through the database once and the csv once. Single pass? Fun. -->