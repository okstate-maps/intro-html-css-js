### Overview of the workshop
1. A whirlwind overview of JavaScript, HTML, and CSS.  
2. Putting all three to work by making a webpage containing text, an image, and an interactive web map.
3. Publishing your webpage on GitHub Pages.
4. Resources for further learning.

### What is HTML?

HTML stands for HyperText Markup Language. At its heart, HTML is used to give *structure* to text and other content. If you think of a website as a house, then you can picture the HTML as the framing.

<img src="https://farm7.staticflickr.com/6221/6334296225_880c0d9acf.jpg" width="500" height="333" alt="Mueller House Condominiums Framing">

### Anatomy of a web page
1. In the beginning, there was the DOCTYPE.
  ```html
  <!DOCTYPE html>
  ```
  
Any self-respecting `.html` file must begin with a declaration to the world what sort of document it is. While there exists a [wide variety](https://en.wikipedia.org/wiki/Document_type_declaration) of doctypes, the **only one** you need to concern yourself with is just plain old `html`. With the advent of HTML5 (the 5th version of the specification for the markup language HTML), it's not really worth too much of your time thinking about the DOCTYPE. It's one of those things that's useless, but still required.

2. Following the DOCTYPE, you will see the first *element* of your webpage, called `html` which contains everything other than the DOCTYPE declaration. 

Here's a graphical breakdown of what makes an HTML element.

![html tag](https://mdn.mozillademos.org/files/9347/grumpy-cat-small.png) 
Source: https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics#Anatomy_of_an_HTML_element

Elements *that will contain other elements* consist of opening and closing *tags*. The opening tag consists of the element's name wrapped in `<` and `>`, while the closing tag wraps the element name in `</` and `>`.  So, at this point your `.html` file would look like this:

```html
<!DOCTYPE html>
<html>
	
</html>
```

![html_tag_w_attrib](https://mdn.mozillademos.org/files/9345/grumpy-cat-attribute-small.png) 

Attributes contain extra information about the element.

3. Next, you will encounter the first *nested* element of your document, called the `head`. The `head` contains metadata about your web page. Some of these elements, such as `meta`, do not contain text or other elements, and as such do not use closing tags. The `head` can contain the following (not an exhaustive list):
  + `<title>`, which is what you see in the browser tab and search results. This is a very important element of a professional looking site and easily overlooked. 
  ```html
    <title>My website</title>
  ```
  + Various `<meta>` elements with different `attributes` such as `name` and `content`. These include `viewport`, which is *crucial* for mobile web development, and `charset`, which is *crucial* if you are working with diacritics (e.g. á or ö). Those two should be included in just about any web page you make.
  ```html
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
  ```
  + `<link>` elements to point to `stylesheets`, which are `.css` files, telling the browser loading your page how to style the content contained in the HTML. Should the text be red or black? 12px or 100px? The `href` attribute is where you put the URL to the stylesheet in question. Below is an example that references the stylesheet used by Leaflet, the popular open source mapping tool we will use later:
  ```html
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.3.4/dist/leaflet.css">
  ```
  + `<style>` element is a way to use CSS within your HTML, rather than storing it in a separate CSS file. It's really just a matter of convenience. It can be a good idea to keep your CSS, HTML, and JS in separate files (if only because it opens up lots of text editor features), but for the purposes of this workshop we'll keep everything in a single `html` file.
  + `<script>` elements allow you to incorporate JavaScript into your web page. Either directly:
  ```html
  <script>alert("Where in the world is Carmen San Diego?");</script>
  ```
   or by supplying a URL via a `src` attribute (similar to `<link>`s use of the `href` attribute). Again, the example below is for Leaflet.

   ```html
   <script src="https://unpkg.com/leaflet@1.3.4/dist/leaflet.js"></script>
   ```

Note that the `script` tag *always requires* both an opening and closing tag!

Taken all together, the `DOCTYPE`, `<html>`, and `<head>` will look something like this. Note the indentation of `<head>` and subsequent elements within it, which is a common convention but not required. Indenting elements contained within other elements makes your HTML much more readable:

```html
<!DOCTYPE html>
<html>
	<head>
		<title>My website</title>
		<meta charset="utf-8" />
    		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<link rel="stylesheet" href="https://unpkg.com/leaflet@1.3.4/dist/leaflet.css">
		<script src="https://unpkg.com/leaflet@1.3.4/dist/leaflet.js"></script>
	</head>
</html>
```

4. The main attraction of any HTML page is the `<body>`. This is where the actual content of your page goes. Everything within your `<body>` is called an *element*. There are [waaaay too many](https://developer.mozilla.org/en-US/docs/Web/HTML/Element) elements to cover in this workshop, but there are just a few groups you need to get started.

#### Text elements

##### Headings (`<h1> - <h6>`)
Headings allow you to label different parts of your webpage in order of importance. For example, `<h1>` should be reserved for the title of the page, or whatever is the most important text.

```html
<h1> The main headline of my website </h1>
```

https://codepen.io/krdyke/pen/WLmxLB

##### Paragraphs `<p>`
The paragraph element is perhaps the most common text element you'll come across. It is used for blocks of text. Note that one feature of `<p>` is that after closing one (using `</p>`), there will be a line break.

```html
<p>
no, money down! silicon chips and such posturologists scratchtasia well, you all know what laughter sounds like. lupper highway 9 bird sanctuary science pole scientician totally outrageous paradigm dealie smokesperson neglecterino beginualize four krustys crayola oblongata smuggled vegetables lisa, go to your room lord protect this rocket house the congealed group paraplegiarino bort boostafazoo knifey wifey baby guts nulecule dorkus molorkus pricetaggery bartesque here's vanessa williams genius at work dirty, maybe. dangerous, hardly.
</p>
```

https://codepen.io/krdyke/pen/GPeqXG

##### Anchors `<a>` (links)
The anchor element is used to link to other websites or sections of your webpage. They need to wrap around existing elements (or part of them). 

```html
<p> This is a paragraph containing an <a href="http://info.library.okstate.edu/map-room">anchor</a>.</p>
```

It does not have to be a paragraph element. Also, if you include `target="_blank"`, clicking the link opens it in a new tab. Very useful!

```html
<h3> Here's a <a href="http://library.okstate.edu" target="_blank">link</a> within a heading that opens in a new tab </h3>
```

If you assign an element an `id`, you can use an anchor to scroll the user back to it when clicked. This is how "Back to top" links are created.

```html
<h1 id="top">Top of document</h1>

... bunch of content ...

<p><a href="#top">Back to top</a></p>

```

https://codepen.io/krdyke/pen/MLYgZW

##### Line Break `<br>`
A crucial element for reproducing something like a poem or address, `<br>` is the equivalent of hitting the enter key. However, do not use `<br>` to separate paragraphs. That's what the `<p>` is for!

```html
Kevin Dyke <br>
123 Fake Street <br>
Stillwater, OK 74078
```

https://codepen.io/krdyke/pen/RvPwXv

#### Media

##### Images `<img>`

Use the image element to add an image. the `src` attribute points to where the image exists. It's important to note that if the image is not on the same server as your website, it may not link. Especially if you're linking to a website that's not specifically made for sharing images (like the Giphy example below).

```html
<img src="https://media.giphy.com/media/26hiu1Oj15ePpkJnG/giphy.gif">
```

https://codepen.io/krdyke/pen/daPyve

You can adjust the size of an image using CSS. The easiest way is to assign an ID to the img element and then style that ID.

```html
<img id="some-name" src="https://media.giphy.com/media/26hiu1Oj15ePpkJnG/giphy.gif">
```

```css
#some-name {
  height:75px;
  }
```

https://codepen.io/krdyke/pen/daPyZK

If you set the height, by default the width will change accordingly to maintain the original aspect ratio. 

*Note:* If you're making an image drastically smaller than its actual size, you should consider creating a smaller version of the image, to improve load times and save user's data.

##### Video `<video>`

The video element can be used to play videos. Generally, this does not apply to Youtube/Vimeo videos. These services generally use Iframes (see the next section).

```html
<video controls src="https://archive.org/download/BigBuckBunny_124/Content/big_buck_bunny_720p_surround.mp4"
    poster="https://peach.blender.org/wp-content/uploads/title_anouncement.jpg?x11217"
    width="620">

Sorry, your browser doesn't support embedded videos, 
but don't worry, you can <a href="https://archive.org/details/BigBuckBunny_124">download it</a> 
and watch it with your favorite video player!

</video>
```

https://codepen.io/krdyke/pen/pGvJZm

##### Iframes `<iframe>`

Iframes are used to embed content from other websites. This can be an entire site, but much more commonly these are used for customized embeds from sites such as YouTube.

A basic example for a random website
```html
<iframe width="860" height="515" src="http://info.library.okstate.edu/map-room"
```

A YouTube provided example
```html
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/Z9N4xFh43os" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
```

https://codepen.io/krdyke/pen/KJwpLO

#### Structural
These are slightly more abstract elements. They are used to structure the logical flow of your website, which is very important for the purposes of accessibility (for example, users using screen-readers).

##### Division `<div>`
A div is used to divide content on your site. As an abstract element, by itself you won't see anything. It's useful for grouping multiple elements into logical groups, particularly when it comes to applying styling via CSS. When possible, you ought to try and use more specific designators, such as `<article>`, `<main>`, `<header>`, `<footer>`, and `<nav>`. We won't cover each of those in detail, but check out [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element) for information about each.

##### Span `<span>`
Similar to a div, except that it functions as an *inline* element. For example, if you wanted to alter the text within a `<p>` element, you would use a `<span>`.

https://codepen.io/krdyke/pen/EraVbv

#### Input `<input>`

##### Button `<button>` or `<input type="button">`

In general, you should use the `<button>` element, as it's much easier to customize the style of.

```html
<button id="red-alert" type="button" onclick="alert('you clicked the button!');">Press me</button>
```

https://codepen.io/krdyke/pen/aXzdbK

##### Radio `<input type="radio">`
Use radio buttons when you want users to pick one (and only one) option among several. You create a `radio group` by making multiple `input` elements and setting the `name` attribute to the same value.

```html
 <input type="radio" id="color1"
   name="favorite-color" value="red">
 <label for="color1">Red</label>

 <input type="radio" id="color2"
   name="favorite-color" value="blue">
 <label for="color2">Blue</label>

 <input type="radio" id="color3"
   name="favorite-color" value="pink">
 <label for="color3">Pink</label>
```

https://codepen.io/krdyke/pen/JxoGOz

##### Checkbox `<input type="checkbox">`
Checkboxes are useful for anything that can be answered true/false, or exists in an on/off state. They're similar to radio buttons, but they don't have a relationship to one another, so the `name` attribute should be different for each.

```html
 <input type="checkbox" id="color1"
   name="checkbox1" value="red">
 <label for="color1">Red</label>

 <input type="checkbox" id="color2"
   name="checkbox2" value="blue">
 <label for="color2">Blue</label>

 <input type="checkbox" id="color3"
   name="checkbox3" value="green">
 <label for="color3">Green</label>
```

https://codepen.io/krdyke/pen/qgdENM

##### Text `<input type="text">`

```html
<label for="name">Name:</label>

<input type="text" id="name" name="name" required size="15">
```

```html
<label for="name">Describe your ideal meal:</label>

<textarea id="meal" name="meal" rows="3" cols="20"></textarea>
```

https://codepen.io/krdyke/pen/aXOvNm

##### Label `<label for="id of the input to label">`

Labels are great and make your site more usable bacause the label adds additional clickable space for your input.

See this comparison.

https://codepen.io/krdyke/pen/daoYem

### CSS
Cascading Style Sheets (CSS) allow you to apply a set of *declarations* to your content, which will be used to determine its appearance. 

CSS is applied according to *declarations* you specify. An example of a CSS declaration is `color: red`, which references the *property* called `color` and sets it to red. The elements these declarations get applied to is decided using *selectors*. 

The following link is a reference to *every available CSS property*. Chances are you'll never use many of these, but whenever you need to check or recheck something, this is a great starting point.

https://developer.mozilla.org/en-US/docs/Web/CSS/Reference

#### Selectors
Selectors consist of element types, classes, ids, or a combination of these. For example, to select all `h1` elements, you'd use a selector like this.

```css
h1 {

}
```

The {} after `h1` indicates a *block* where your *declarations* will go. A CSS declaration has the following structure:

![declaration](https://mdn.mozillademos.org/files/3665/css%20syntax%20-%20declaration.png)
Source: [MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Syntax#CSS_declarations)

Thus, if we wanted all `h1` elements to have red text, the selector, block, and declaration would look like this.

```css
h1 {
	color: red;
}
```

Selectors can be grouped using commas to apply the same declarations to different elements. For example to apply the `color: red` declaration to multiple types of headings, you'd use:

```css
h1, h2, h3 {
	color: red;
}
```

See how it works below.

https://codepen.io/krdyke/pen/QzogVR

While using just element names to set style rules is useful, you quickly encounter the case where you need to get more specific.

#### Classes

Classes are a marvelous way to group CSS declarations. They can save you a lot of text and also make updating your site much faster. Classes are set on html elements using the `class` attribute. They are referenced in CSS by a `.` in front of the name.

For example:

```html
<h1> I want to make the word <span class="text-red">red</span> appear <span class="text-red">red</span>. </h1>  
```

The two `span` elements both have a class attribute set to `text-red`. The accompanying CSS would look like this:

```css
.text-red {
	color: red;
}
```

Let's see it in action.

https://codepen.io/krdyke/pen/ErjPVo

#### IDs
In the input examples, you may have noticed some JavaScript containing phrases like `$("#name")`. The `#` is how you refer to an element by ID. Unlike classes, IDs should be unique to your webpage. Thus, you don't want to rely on them for CSS. They work best in combination with classes. Duplicate IDs won't necessarily break your page, but will result in unpredictable behavior.

https://codepen.io/krdyke/pen/wNaMWa

#### Nested Selectors
You can use spaces to combine multiple selectors to make a single, more *specific* selector.

https://codepen.io/krdyke/pen/JxdXyj

#### Specificity
You can combine some selectors, such as element and class, as well. Most newcomers to CSS get caught up by styles not being applied when you think they should be. To avoid this problem, it's very helpful to get proficient with *selector specificity*, which is the mechanism by which your browser decides which CSS declaration to actually use when styling a page. This article from [CSS Tricks](https://css-tricks.com/specifics-on-css-specificity/) can be helpful. Here's an example of what I mean by specificity. Say you have a header element like this:

```html
<h1 id="greeting" class="cowboy-greeting">Howdy</h1>
```

Accompanying the `html`, you have the following `css` *declarations*:

```css
h1.cowboy-greeting {
  color: red;
}

#greeting {
  color:green;
}

.cowboy-greeting {
  color: blue;
}
```

What color do you think the word "Howdy" will look like?

Take a look.

https://codepen.io/krdyke/pen/GzJZxE

Having a sense of how selectors work and how specificity comes into play will save you *many* headaches down the line.

#### Advanced Layout using CSS Grid
Using CSS create webpage layouts can be a real pain. Luckily for us, a new feature called the CSS Grid makes layout much less painful. In particular, I like using what's called the template areas approach. If you have HTML such as this.

```html
<header> Name of your site.</header>
<nav> Navigation area </nav>
<sidebar>Ancillary content</sidebar>
<main>The main event</main>
<footer>Bottom of content</footer>
```

You can use CSS Grid to create an interesting layout like this:

![Layout](/img/grid_layout.jpg?raw=true "An Interesting Layout")

Look at this link to see how. Note that this may be confusing at first, but don't despair.

https://codepen.io/krdyke/pen/zeGBmw

For more about laying out a page using CSS see this page.

https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Introduction

### JavaScript and JQuery

#### variables 
- create an empty variable using `var <name of variable>;` 
- create and set a value using `var <name of variable> = <value of variable>;`
- you can change the value of a variable anytime, to anything. This isn't legal in some other languages (like Java), but for the most part, it's a big time saver for our purposes.

#### functions
- create them like this `function sayHello(){alert("hi")};`
- or like this `var foobar = function(){alert("hi")};
- execute a function like this `sayHello()`
- [**scope**](http://www.smashingmagazine.com/2009/08/what-you-need-to-know-about-javascript-scope/) is an important concept!
  - most importantly, any variable defined within a function is only "visible" within that function. If you try to access it elsewhere, you'll get an error. This means you really need to be careful about how you assign `var` statements. If you refer to a variable without one, it's implied you wanted to create a *global variable*, which is a variable accessible from anywhere. For example:

```javascript
var fruit = "persimmon";

var func1 = function (){
    var fruit = "ugli fruit";
};

var func2 = function (){
    fruit = "kumquat";
};
console.log("1: " + fruit);

func1();

console.log("2: " + fruit);

func2();

console.log("3: " + fruit);

//what is going on here??
```

https://codepen.io/krdyke/pen/qgdrpQ?editors=0011


#### [JQuery](http://jquery.com)
##### Tagline: "write less, do more"
JQuery is a swiss army knife for working with JavaScript. An example:

```javascript
//plain old javascript
var ele = document.getElementById("someElement");
ele.style["background-color"] = "red";

//JQuery
$("#someElement").css("background-color", "red");

//these both do the same, but JQuery is a lot more space friendly. The real 
//power comes in with more complicated selections. The $("") clause lets select 
//elements in the DOM using CSS selectors.
```

##### loops
Take an array such as this
```javascript
var fruits = ["apple", "orange", "kiwi", "grapefruit"];
```

To loop through this array using plain javascript, you'd do something like this:

```javascript
for (var i = 0; i < fruits.length; i++){
  console.log(fruits[i]);
}
```

Which is really weird looking. With JQuery, it's more straightforward (once you get a hang of the syntax). JQuery uses:

```javascript
$(fruits).each(function(index, item){
  console.log(item);
});
```

##### Events
JQuery is used a lot to handle *events*. JavaScript is called an *event driven language*, because most of it is written to respond to events such as a user clicking somewhere, or dragging, or typing on the keyboard. JQuery can be used to do something when a user clicks on an element selection. 

```javascript
$("#some-id").click(function(event){ // this function is called a handler
  //do something with the click
  alert("Someone clicked! Red alert!");
  $("body").css("background-color", "red");
})
```

https://codepen.io/krdyke/pen/jdPBXL

##### AJAX
For our purposes, a really important aspect of JQuery is the ability to make AJAX requests. AJAX originally meant Asynchronous JavaScript and XML, but it now more generally refers to asynchronous JavaScript stuff. Web maps are all examples of asynchronous JavaScript in action.

AJAX is what you use to fetch data.

##### An interlude to talk about JSON and GeoJSON
JSON (and its derivative geofocused cousin GeoJSON) are **data exchange formats** that emphasize human readability and conciseness. JSON is **the** standard on the web for moving data around (having replaced XML), and GeoJSON is quickly getting to that point for spatial data.

Take this table (think of it as a spreadsheet:

Type   | Squishiness      | Color
-------|------------------|-------
apple  | not squishy      | red
banana | very squishy     | yellow
kiwi   | somewhat squishy | brown

If we looked at that as JSON, it would look like this:

```json
{"fruits":[
    {"type":"apple", "squishiness":"not squishy", "color": "red"},
    {"type":"banana", "squishiness":"very squishy", "color": "yellow"},
    {"type":"kiwi", "squishiness":"somewhat squishy", "color": "brown"}
]}
```

JSON allows you to *nest* data, making it far more flexible than a row based spreadsheet or CSV. For example, GeoJSON looks like this:

```json
{
  "type": "Feature",
  "properties": {
    "route_number": "22",
    "category": "bus stop"
  },
  "geometry": {
    "type": "Point",
    "coordinates": [
      -93.24751138687132,
      44.971249995945435
    ]
  }
}
```

If you ever interact with an API (which stands for Application Programming Interface), it will 99% of the time be in the form of JSON. 

Some popular APIs include those provided by Twitter and GitHub.

Let's take a quick look at some JSON via the GitHub API.
https://codepen.io/krdyke/pen/xMGjgj?editors=0011

##### Making a map

Let's go to https://codepen.io/krdyke/pen/yZYJEL and make a map.

#### Using GitHub Pages to host your site for free
1. Login to GitHub
2. Create a new repository, called `intro-webdev`. Click yes to create README
3. Click Settings, scroll down to GitHub Pages, change Source to master branch. Click Save.
4. In new repository, click Create New File.
5. Call it index.html and follow the steps below to make it come to life!

#### Let's bring it all together
Using what we learned today, let's build a webpage with the following elements.

1. HTML content including:
  - DOCTYPE
  - head element
    + meta element for charset
    + meta element for viewport
    + Link element pointing to leaflet.css
      + `<link rel="stylesheet" href="https://unpkg.com/leaflet@1.4.0/dist/leaflet.css">`   
  - body element
    + div element with `id` set to `map-container`
    + div element with `class` set to `red box`
    + Script tags linking to leaflet and jquery.  
      ```
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
	  <script src="https://unpkg.com/leaflet@1.4.0/dist/leaflet.js"></script>
       ```
     
2. CSS declarations
  - a declaration for the id `map-container` that sets the `height` to `400px;` and the `width` to `500px;`
  - a declaration for the class `box` setting `height` to `200px;` and `width` to `200px;`
  - a declaration for the class `red` setting `background-color` to `tomato;` and `border` to `3px double red;` 

3. JavaScript
  - create a Leaflet map (`L.map`) 
  - set the initial view to 36.12250, -97.06997 and zoom level 14 (`L.setView`)
  - add a basemap using the url `https://api.mapbox.com/styles/v1/krdyke/cj8uh9ex2e8x72ss197dx81n0/tiles/256/{z}/{x}/{y}?access_token=pk.eyJ1Ijoia3JkeWtlIiwiYSI6Ik15RGcwZGMifQ.IR_NpAqXL1ro8mFeTIdif` (`L.tileLayer`)
  - add a marker at Edmon Low Library
  	- `L.marker([36.123080, -97.069668]).addTo(map)`
  	
  - Use JQuery to select the div with `class` set to `red box`
    + Use the selector `.red.box` 
    + Add a click handler (`$(<your selector>).click(function(e){<doing something>})`) that does something in response to a user clicking on the div

#### "Extra Credit"
  - add a button to your html that when clicked will request GeoJSON and add it as a layer to the map
  - add a button to your html that when clicked will announce the current time and date
  - add a layer switcher control to your map and an additional basemap
  - request and add a GeoJSON layer using the relative url `green-line-eastbound.geojson`
  - add more GeoJSON from the url `http://opendata.minneapolismn.gov/datasets/cb8d4b1dbad0470380e5f46f1e75e962_0.geojson` 
    + attach a popup to each feature that displays the station name
    + style each feature to be red circle instead of the default blue marker

#### Some guidelines
You're going to need to read documentation ([Leaflet's](http://leafletjs.com/reference.html) especially), review what we've done, look at some source code, and ask each other some questions. The console (F12 or ctrl-shift-I (Windows) or cmd-shift-I (Mac)) is your friend!


#### Optional materials for learning more HTML, CSS, JS, and JQuery
This Khan Academy course is excellent. If you have any doubts about your profiency with this stuff, please complete this course for next week.  
https://www.khanacademy.org/computing/computer-programming/html-css

Same goes for the tutorials from the Mozilla Developer Network.  
https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web

And a JQuery tutorial. It can do a lot of stuff.  
https://learn.jquery.com/about-jquery/how-jquery-works/

HTML Reference
https://developer.mozilla.org/en-US/docs/Web/HTML/Element

CSS Reference
https://developer.mozilla.org/en-US/docs/Web/CSS/Reference

JS Reference
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference

#### Cheat Sheets!
https://htmlcheatsheet.com/
https://www.smashingmagazine.com/2009/07/css-3-cheat-sheet-pdf/
https://websitesetup.org/javascript-cheat-sheet/

#### Workshop evaluation
https://okstate.libsurveys.com/webdev-101
