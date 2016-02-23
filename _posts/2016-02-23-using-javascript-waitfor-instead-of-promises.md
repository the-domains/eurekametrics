---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: ''
datePublished: '2016-02-23T17:56:32.865Z'
dateModified: '2016-02-23T17:55:10.928Z'
title: Using Javascript waitFor() instead of Promises
author: []
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
sourcePath: _posts/2016-02-23-using-javascript-waitfor-instead-of-promises.md
published: true
url: using-javascript-waitfor-instead-of-promises/index.html
_type: Article

---
Efficient wait/timeouts in Javascript

It's pretty common knowledge that Javascript's handling of async events is funky.  Everyone has spent their time in callback hell.  Promises and Observables are nice, but they're not a universal solution.  I spent a good hour searching for alternatives to sleep() in Javascript, and came up woefully empty.

So here's the problem I'm working on today:  What if I need to do something after loading two different async resources independently?  For instance, when I want to compare the results from two separate REST web services, I'll have to wait for each resource to load, and then run my action. 

Using regular callbacks or promises, this gets ugly fast.

After some tinkering, my solution is to use window.setTimeout() to poll until a condition is met, and then trigger the response.  Yes, polling is usually a no-no, but it's working great in  my test cases.  So, I thought I'd share it here and see if it helps anyone else.