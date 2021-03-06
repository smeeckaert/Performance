perf-tool
===
What is this:<br>
Demo:<br>
[**http://performance.devbproto.com/**](http://performance.devbproto.com/)<br>
[**Landing page**](http://devbridge.github.io/Performance/)<br>

---
**In short about:**<br>
This is a npm package to display statistics about your web pages, information such as css resources count, Google PageSpeed Insights score, information how to fix performace issues, html errors and many more in one custom web page.

**Tech details:**<br>
This package mainly uses three plugins [**w3cjs**](https://www.npmjs.com/package/w3cjs) (html test errors, warnings ect), [**Google PageSpeed Insights**](https://developers.google.com/speed/pagespeed/insights) (a lot information, for example: how to fix main load/performance issues, load times...) and [**dev-perf**](https://github.com/gmetais/grunt-devperf) (number of 404 errors, number of images without dimensions ect). Then colected that information is displayed in angular js based web page.

---
Usage:
---


**Setting up:**

Firstly install this package locally to your project:
```
npm install devbridge-perf-tool --save-dev
```

And add it to your gulpfile.js:

```javascript
require('gulp').task('perf-tool', function () {
	var options = {
    	siteURL:'http://www.google.com',
        sitePages: ['/', '/voice']
	};
	return require('devbridge-perf-tool').performance(options);
});
```
After running this task, launch browser and go to your hosted website with installed perf-tool by the folowing url: **```YourHost/perf-tool```** (example: ```localhost/perf-tool```, you can change directory ```perf-tool``` by changing property ```options.resultsFolder```)<br>
**Available options:**<br>
List of available options to configure and change behavior of perf-tool.<br><br>

**options.siteURL** <br>
**Type:** ```string```<br>
**Default value:** ```""``` (Empty string)<br>
**Description:** Used for site base url. You can change it depending by envirioment (dev, staging, live this is recommended) or leave empty and use full urls in **options.sitePages** (next option), urls must start with protocol (example: ```http://```).<br><br>

**options.sitePages** <br>
**Type:** ```string [ ]```<br>
**Default value:** ```[ ]``` (Empty array)<br>
**Description:** Used to generate site map with **options.siteURL** (example: ```options.siteURL + options.sitePages[i]``` ). You can use full urls (example: ```options.sitePages = ['http://www.google.com/voice']```) by leaving options.siteURL empty or set options.siteURL and pages (example: ```options.siteURL='http://www.google.com'; options.sitePages = ['/','/voice'];``` ).<br><br>

**options.runDevPerf** <br>
**Type:** ```bool```<br>
**Default value:** ```true```<br>
**Description:** You can disable [dev-perf](https://github.com/gmetais/grunt-devperf) if it's information is not needed for you.<br><br>

**options.runHtmlTest** <br>
**Type:** ```bool```<br>
**Default value:** ```true```<br>
**Description:** You can disable [w3cjs](https://www.npmjs.com/package/w3cjs) if it's information is not needed for you.<br><br>

**options.runGoogleSpeedTest** <br>
**Type:** ```bool```<br>
**Default value:** ```true```<br>
**Description:** You can disable [Google PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights) if it's information is not needed for you but it is **not recommended**.<br><br>

**options.googleAPIKey** <br>
**Type:** ```string```<br>
**Default value:** ```""``` (Empty string)<br>
**Description:** To test this app you can not set it, but latter on for live envirioments please set it.<br><br>

**options.resultsFolder** <br>
**Type:** ```string```<br>
**Default value:** ```"./perf-tool"```<br>
**Description:** Folder where collected results formated by this task are put (if folder does not exist it will be created, but path where it is created is not checked).<br><br>

**options.smallerDevperfOutput** <br>
**Type:** ```bool```<br>
**Default value:** ```true```<br>
**Description:** Whether or not make devperf output smaller (while runing task and [dev-perf](https://github.com/gmetais/grunt-devperf) writes to console).<br><br>

**options.logFilterKeys** <br>
**Type:** ```bool```<br>
**Default value:** ```false```<br>
**Description:** Whether or not webpage will log **filter keys** (explanaition on next option) to console.<br><br>

**options.minimumPassScore** <br>
**Type:** ```int```<br>
**Default value:** ```80```<br>
**Description:** Minimum pass score ([Google PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights) score), failed pass minimum score results will be marked red.<br><br>

**options.translations** <br>
**Type:** ```dictionary```<br>
**Description:** this is a dictionary with key **```filter key```** and value either ```string``` or ```bool false```. It is used for displaying human readable names for collected information or disaibling it by setting it's value to false, if no name is found in current (user defined dictionary) it is searched in default distionary ```./node_modules/devbridge-perf-tool/settings.txt``` if value not found it is autogenerated by magical function.<br>
**Example:**<br>
```
options.translations = {
	"desktop.formattedResults.locale":"Locale",
    "devperf.ajaxRequests":"Ajax Requests",
    "html.context.old":false
};
```


[![Analytics](https://ga-beacon.appspot.com/UA-73039601-3/Performance/readme)](https://github.com/igrigorik/ga-beacon)
