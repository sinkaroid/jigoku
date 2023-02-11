<div align="center">
<a href="https://github.com/sinkaroid/jigoku/wiki"><img width="500" src="https://cdn.discordapp.com/attachments/1046495201176334467/1048406208714903635/jigoku_.png" alt="jigoku"></a>

<h4 align="center">Bulk downloader for booru imageboards with evil intentions</h4>
<p align="center">
	<a href="https://github.com/sinkaroid/jigoku/actions/workflows/jigoku_posts.yml"><img src="https://github.com/sinkaroid/jigoku/workflows/bulk%20multiple%20posts/badge.svg" /></a>
	<a href="https://github.com/sinkaroid/jigoku/actions/workflows/jigoku_pages.yml"><img src="https://github.com/sinkaroid/jigoku/workflows/bulk%20multiple%20pages/badge.svg"></a>
</p>

Jigoku is a CLI tool for downloading content around the imageboards, seamlessly integrates with popular website like danbooru, rule34, gelbooru, and many more. It's also modular, no matter what kind of links you have, what kind imageboard you want to download from, If still covered by the flow, this tools will adapt.

<a href="#usage">🚀 Usage</a> •
<a href="https://github.com/sinkaroid/jigoku/actions">Testing Cases</a> •
<a href="https://github.com/sinkaroid/jigoku/wiki">Documentation</a> •
<a href="https://github.com/sinkaroid/jigoku/issues/new/choose">Report Issues</a>

</div>

- [Jigoku](#)
  - [The problem](#the-problem)
  - [The solution](#the-solution)
  - [Features](#features)
    - [Site support](#site-support)
  - [Installation](#installation)
    - [Prerequisites](#prerequisites)
    - [Usage](#usage)
  - [Running tests](#Running-tests)
    - [Phrases](#phrases)
  - [Limitations](#limitations)
  - [Pronunciation](#Pronunciation)
  - [Legal](#legal)

---

## The Problem

<img src="https://cdn.discordapp.com/attachments/1046495201176334467/1049067378224410785/Screenshot_70.png" width="800" alt="jigoku">
<img align="right" src="https://cdn.discordapp.com/attachments/1046495201176334467/1049104637313167380/pain_peko.png" width="80">  

Hell opening fuckton of tabs, and download them one by one. Piece of crap  
Welp, It's not tough actually if still same website, there is also tampermonkey hacks to mock them, but what if you want to get 'em from multiple websites?


## The Solution
<img src="https://cdn.discordapp.com/attachments/1046495201176334467/1049089263247032370/jigoku_flow_1.png" width="800" alt="jigoku">


No more tampermonkey hacks, no more opening a fuckton of tabs, no more spliting your note between danbooru, gelbooru, r34 or anything else. Just one command through single file, this tools will adapt.  

Jigoku apply connection retry on failed, every your network changes or something else, It will keep waiting. 

## Features
- Modular bulk download
- 75% tested
- Plenty of booru support
- Connection retry on failure
- Pure scraping, does not hit the API
- Download with ease
- Interactive prompt

## Site support

Jigoku supports the following imageboards:

- [rule34](https://rule34.xxx/)
- [danbooru](https://danbooru.donmai.us/)
- [gelbooru](https://gelbooru.com/)
- [safebooru](https://safebooru.org/)
- [tbib](https://tbib.org/)
- [xbooru](https://xbooru.com/)
- [realbooru](https://realbooru.com/)
- [yandere](https://yande.re/)
- [lolibooru](https://lolibooru.moe/)
- [konachan](https://konachan.com/)
- [konachan.net](https://konachan.net/)
- [hypnohub](https://hypnohub.net/)
- [e621](https://e621.net/)
- [e926](https://e926.net/)
- [allthefallen](https://booru.allthefallen.moe)
- [paheal](https://rule34.paheal.net/)


## Prerequisites

<table>
	<td><b>NOTE:</b> Python 3.7 or above</td>
</table>

Jigoku depends on
- [requests](https://pypi.org/project/requests/) Python HTTP Client
- [beautifulsoup4](https://pypi.org/project/beautifulsoup4/) HTML Parser

## Installation
It's fairly simple to use jigoku

`pip install jigoku`

- Or manual build by cloning this repository and run `python setup.py install`


## Usage
Just run without any arguments and interactive prompt will get you,  

<img src="https://cdn.discordapp.com/attachments/1046495201176334467/1049111079562784778/17_1.png" width="600" alt="jigoku">  

`$ jigoku`

1. First prompt will ask you to input your file
    - Input your file.txt

2. Second prompt will ask you what kind of links you have
    - `(1)` multiple posts or galleries 
    - `(2)` multiple pages

3. Third prompt will ask you for image resolution
    - `(1)` original, means the original, big size
    - `(2)` sample, means smaller than original

## Running tests
Is current state not covers enough? Feel free to add more test cases and submit a pull request.  

> Multiple posts test: [workflows/jigoku_posts.yml](https://github.com/sinkaroid/jigoku/actions/workflows/jigoku_posts.yml)  
Multiple pages test: [workflows/jigoku_pages.yml](https://github.com/sinkaroid/jigoku/actions/workflows/jigoku_pages.yml)  
Example file input: [jigoku/tree/master/test](https://github.com/sinkaroid/jigoku/tree/master/test)


### Phrases
This pattern used for validating **posts** or **galleries**  

> `/posts/` danbooru based, `&id=` gelbooru based, `?id=` gelbooru based, `/show` yandere based, `/post/view/` paheal based 

Otherwise, it will assign to **pages**

For example, If you confused between `(1)` and `(2)`, check this out:

- `https://danbooru.donmai.us/posts/5874589`
- `https://rule34.xxx/index.php?page=post&s=view&id=7004047`
    - This is post, choose `(1)`
- `https://danbooru.donmai.us/posts?tags=1girl&z=1`
- `https://rule34.xxx/index.php?page=post&s=list&tags=1girl`
    - This is pages, choose `(2)`
- `https://danbooru.donmai.us/posts?tags=kiryuuin_satsuki+&z=5`
- `https://rule34.xxx/index.php?page=post&s=list&tags=kiryuuin_satsuki`
    - This is pages from tags, choose `(2)`
- `https://danbooru.donmai.us/posts?page=2&tags=kiryuuin_satsuki+`
- `https://rule34.xxx/index.php?page=post&s=list&tags=kiryuuin_satsuki&pid=42`
    - This is pages from tags with page number, choose `(2)`
- `https://danbooru.donmai.us/posts?tags=hews+&z=5`
- `https://rule34.xxx/index.php?page=post&s=list&tags=belko`
    - This is pages from artist, choose `(2)`

## Limitations
You may notice that some part were strictly to "Original" resolution and "Sample" is no use, I'm pretty sure there are some limitations, for example old posts perhaps has different structures, but I haven't found any yet, current test cases has over 1000+ posts and took 20+ minutes, and it works fine.

## Legal
This tool can be freely copied, modified, altered, distributed without any attribution whatsoever. However, if you feel
like this tool deserves an attribution, mention it. It won't hurt anybody.
> Licence: WTF.

## Pronunciation
[`ja_JP`](https://www.localeplanet.com/java/ja-JP/index.html) • **jigoku** — 地獄、じごく, meaning "hell". The other mean if you opening fuckton of rule34 on google chrome tabs, then downloading one by one, Definitely hell and piece of crap