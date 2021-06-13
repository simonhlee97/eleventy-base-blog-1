---
title: Date Formats in JavaScript
description: I've always had a hard time remembering how to format dates...
date: 2021-06-13
tags: ['javascript', 'Date-formatting']
layout: layouts/post.njk
---
Choosing a date format is like walking down the cereal aisle, and I've always had a hard time remembering how to format dates. So I wanted to write a quick reference post of my favorite formats.

### Problem: How do I show a reader-friendly date and time on a webpage?

```html
<!-- html -->
<div id="the-date"></div>
```

```js
// javascript
var myDate = document.getElementById('the-date');
myDate.textContent = new Date();
```

Simple enough. But your date will look like this:

```
Sun Jun 13 2021 13:24:58 GMT+0900 (Korean Standard Time)
```

A bit overkill and probably too much for your readers. Our mission is to format the date to something more reader-friendly like "6/13/2021, 1:24:58 PM".

### Solution

The built-in Date object has many methods. `console.log()` it to see the full list. Some of them start with 'to'. By calling one of these methods, you can easily change your date's format.

Go ahead and play around with the 2nd line (from the JS above).

```js
myDate.textContent = new Date().toLocaleString();
// returns 6/13/2021, 1:45:56 PM
```

#### A few more options:

```js
myDate.textContent = new Date().toLocaleDateString()
// returns 6/13/2021

myDate.textContent = new Date().toLocaleTimeString()
// returns 1:56:18 PM

myDate.textContent = new Date().toDateString()
// returns Sun Jun 13 2021

myDate.textContent = new Date().toUTCString()
// returns Sun, 13 Jun 2021 04:54:56 GMT

myDate.textContent = new Date().toISOString()
// returns 2021-06-13T04:56:57.694Z
```

You can also visit the Mozilla Docs for all the different formats.

#### But how do I display a ticking clock with the current date and time?

One possible solution would be JavaScript's `setInterval()` method. If you write a function that displays the current time, and run it every 1 second (or 1000 ms), then you've got a "ticking clock" on your web page.

```js
var myClock = document.getElementById('myClock');

function ticking() {
    myClock.textContent = new Date().toLocaleString();
}

setInterval(ticking, 1000);
```