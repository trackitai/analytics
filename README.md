**The API Reference contains low-level details on TRACKIT APIs and codebase.**

*You will find here documentation on TRACKIT HTTP APIs, JavaScript client integrations, methods and hooks.*

---


## TRACKIT HTTP API

To track page views, events, visits, you have to send a HTTP request (GET) to TRACKIT HTTP API endpoint *(https://trackit.pergatech.com/api/ve/)* with the correct query parameters set.

---


## The JavaScript Tracking Snippet

Adding the following code (known as the *JavaScript tracking snippet*) to your site's templates is the start point for measuring how users interact with your website.

Copy and paste the JavaScript tracking code into your pages, just after the opening `<body>` tag (or within the `<head>` section)

---
```html
<!-- Trackit Analytics -->
<script>
  var _paq = window._paq || [];
  _paq.push(['trackPageView']);
  (function() {
    var u="https://trackit.pergatech.com";
    _paq.push(['setTrackerUrl', u+'/api/ve/{$IDSITE}/']);
    _paq.push(['setSiteId', {$IDSITE}]);
    var d=document, g=d.createElement('script'), s=d.getElementsByTagName('script')[0];
    g.type='text/javascript'; g.async=true; g.defer=true; g.src=u+'/js/v1.0/analytics.js'; s.parentNode.insertBefore(g,s);
  })();
</script>
<!-- End Trackit Analytics -->
```
---

In your tracking code, **{$IDSITE}** would be replaced by the site ID of the website you wish to track. This ID is provided to you.

For asynchronous tracking, configuration and tracking calls are pushed onto the global _paq array for execution, independent of the asynchronous loading of analytics.js. The format is:

---
```javascript
_paq.push([ 'API_method_name', parameter_list ]);
```
---


## JavaScript Tracker Features

---
**Tracking Page Views**

By default, every page having the above javascript code snippet is tracked as visits. TrackitAPI uses the URL of the current page as _visit url_ and title of the page as _visit title_. You can disable this feature by deleting or commenting the code line:

---
```javascript
_paq.push([ 'trackPageView']);
```
---


**Tracking Events**

Once you've added the javaScript tracking snippet to your page and created a tracker, you can create custom events.

TrackitAPI event tracking has the format as following:

---
```javascript
_paq.push(['trackEvent', 'eventCategory', 'eventAction', 'eventName', 'eventValue']);
```
---
and it will log an event with an event category (Forms, Downloads, Videos, Music, Games...), an event action (Submitted, Checked, Downloaded, Clicked...), and an optional event name and optional event value.


**Example Code Blocks**

> Tracking the time your page has fully loaded with custom event:

```html
<!-- Trackit Custom Event -->
<script>
 window.onload = function () {  
  var pageLoadedTime = new Date();
  _paq.push(['trackEvent', 'page', 'onload', 'pageFullyLoaded', pageLoadedTime.getTime()]);
  
  // doSomethingElse();
  // ...
};
</script>
<!-- Trackit Custom Event -->
```
---

> Tracking a button click with custom event:

Suppose you have button in yout html code with id _trackerButton_

```html
<!-- Trackit Custom Event -->
<script>
var button = document.getElementById('trackerButton');
button.addEventListener('click', function () {
  _paq.push(['trackEvent', 'button', 'click', 'optionalButtonEventName', 'optionalButtonEventValue']);
});
</script>
<!-- Trackit Custom Event -->
```

You can check the tamplate files in src directory for full usage experiences.
