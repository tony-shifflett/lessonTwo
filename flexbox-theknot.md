![](/ga_cog.png)

---

Title: Introduction to Flexbox<br>
Duration: "60min"+<br>
Competencies: CSS, Flexbox<br>
Prerequisites: HTML, CSS basics<br>

---

<img src="https://i.ytimg.com/vi/JVYVDpdvdMo/maxresdefault.jpg" width=500/>

## Prerequisites

- Familiarity with display property values such as: block, inline, inline-block

## Objectives

By the end of this you should be able to:

- Know when and where to apply flexbox
- Work with several flexbox properties available to a flexbox container
- Work with several flexbox properties are available to a flexbox child element
- Implement a design using parent and child flexbox properties

## Intro

### A Very Brief History

Flexbox was introduced as part of CSS3 and it's been around since ~2008. Despite being a technology that has been around for nearly 12 years, it lacked consistent browser support (until recently) and thus developers have often had to fall back on some of the following older layout approaches:

- changing and elements `display` property from `inline` to `block`
- using the `float` or `position` property to take an element out of the document flow

[Basics & Terminology Of Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

#### Can I use flexbox?

Flexbox, currently has near universal support from all major modern browsers. You can find out what browsers support by going to [caniuse.com](http://caniuse.com/) , this website also documents support for just about anything else you might want to put in the browser, inclulding HTML and JavaScript.

#### Vendor Prefixes

If you are wondering if you should be using `vendor prefixes` (looks like the code below) and how to write them, a great resourse is [shouldiprefix](http://shouldiprefix.com/):

```
.page-wrap {
  display: -webkit-box;  /* OLD - iOS 6-, Safari 3.1-6, BB7 */
  display: -ms-flexbox;  /* TWEENER - IE 10 */
  display: -webkit-flex; /* NEW - Safari 6.1+. iOS 7.1+, BB10 */
  display: flex;         /* NEW, Spec - Firefox, Chrome, Opera */
}
```

In SEIR we are only worrying about modern browsers and won't be including vendor prefixes in our CSS but we want that you are aware they exist and their purpose.

### Flexbox is its own thing

Flexbox is built with its own logic. Flexbox properties are more descriptive like `justify-content: space-between;` or `flex-direction: column;` with spacing and resizing being calculated under the hood.

Flexbox has just two types of elements, each of which have their own properties.

- `flex container` - `parent`
- `flex items` - `children`

#### Flexbox Axes

Flexbox is one dimensional in that it either applies to elements in a `row` or `column`.  If working on a `row` the `main axis` is horizontal however if set to `column` the `main axis` will be vertical.  

<img src="https://i.imgur.com/8vyhPm1.png" width=500/>

#### Flexbox Playground

During the lesson we will use [Flexbox Playground](https://codepen.io/jkeohan/live/zdKJOY) to explore the flexbox settings and their effect. 

### Use Case for Flexbox

One great use case for flexbox is a layout pattern that is often referred to as `cards`. Cards are often used to advertise services on a company web site or display products for an online shopping.

<hr>

#### <g-emoji class="g-emoji" alias="alarm_clock" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/23f0.png">⏰</g-emoji> Activity

One site that represents a modern layout and is a beautifully desinged is [The Knot](https://www.theknot.com/).

- Let's take a look at the site
- On the home page we should see the services section towards the bottom
- Examine how the responsiveness of the those elements by decreasing the page width

<hr>

### What We Are Building Today

Below is our attempt at redesigning the services section of The Knot and what we will focus on building today. We will be using Flexbox to position the elements, define their widths as well as add some responsiveness.

The desktop version would be displayed as 2 rows and 4 columns.

<img src="https://i.imgur.com/KqObq8S.png" width=600/>

The responsive versions will work for mobile and tablet.

<img src="https://i.imgur.com/kWSxtU4.png" width=600/>

### Getting Started

#### Starter-Code Directory

- Navigate to the starter-code-theknot directory
- Inside we will find the following - `index.html` - it is already set up for you - `default.css` - a little bit of css to get us started - it is already set up for you - `main.css` - this is the **ONLY** file that you will be coding in for this morning's exercise

Open `index.html` in your browser and it should look like below.

<img src="" width=500/>

#### Examine The HTML

Let's take a moment to examine the `index.html` file. In the `head` we will see some additional css being imported for [Font Awesome](). It's and online library that provides many free icons.

```html
<!-- FONT AWESOME -->
<link
	rel="stylesheet"
	href="https://use.fontawesome.com/releases/v5.2.0/css/all.css"
/>
<link
	rel="stylesheet"
	href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css"
/>
```

Then links to our css. For this codealong we will only be editing `main.css.`

```html
<!-- OUR CSS -->
<link rel="stylesheet" href="default.css" />
<link rel="stylesheet" href="main.css" />
```

The main section that contains the `nav > ul > li` elements.

```html
<nav class="ListContainer">
	<ul>
		<li class="ItemContainer">
			<a href="#">
				<div class="ImageContainer"><i class="far fa-heart fa-2x"></i></div>
				<div class="ItemContentContainer">
					<h4 class="ItemHeader">Wedding Vision</h4>
					<p class="ItemHeading">
						Define your wedding style and get matched with local vendors.
					</p>
				</div>
			</a>
		</li>
	</ul>
</nav>
```

### Getting Started

Open the `main.css` file that as we will be writing all our CSS there.

By default HTML applies some default CSS which we can clearly see being represented here as the `dot` and spacing between the elements.

<img src="https://i.imgur.com/g1FVOz9.png" width=500/>



There are times when front end devs want to start with a clean slate and so they add CSS that removes the defaults being applied. Lucky for us there is a css library that does that for us already, it's called `reset.css`

Let's add the following link tag to the head.

```html
<!-- RESET CSS -->
<link
	rel="stylesheet"
	href="https://cdnjs.cloudflare.com/ajax/libs/meyer-reset/2.0/reset.min.css"
/>
```

Once applied we should see the HTML updated to be the following.

<img src="https://i.imgur.com/ABt6lms.png" width=500/>

#### Borders...Borders...Borders..

Before we define any additional CSS settings let's turn on borders for all elements so we can clearly see their dimensions.

```
* {
  border: 1px solid;
}
```

Hmmm...why didn't that apply? Any ideas?...

<hr>

#### <g-emoji class="g-emoji" alias="alarm_clock" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/23f0.png">⏰</g-emoji> Activity - 5min

- Take a moment to examine the elements in DevTools
- Review both the `Styles` and `Computed` tabs and see if they provide any insight.

<hr>

#### The `!important` Flag

We can fix this by adding the `!important` flag to make this setting take precedence.

```css
* {
	border: 1px solid !important;
}
```

<img src="https://i.imgur.com/Trk3pkT.png" width=500/>

#### Center The Nav

We can horizontally center the nav by assigning it a width and a margin.

```css
nav.ListContainer {
	max-width: 800px;
	margin: 0 auto;
}
```

### Adding Flexbox

You have already been exposed to the display property and that elements are assigned a default value of either `inline` or `block` by default. Another value that we can assign to the display property is `flex`.

The main properties that are specific to the to the `flex` parent are:

| Property        | What's It Do?                           | Examples                                  |
| --------------- | --------------------------------------- | ----------------------------------------- |
| display         | Turns on flexbox                        | `flex`                                    |
| flex-direction  | Sets the directional flow of flex items | `row`, `column`                           |
| justify-content | Align along main axis                   | `center`, `space-between`, `space-around` |
| align-items     | Align along cross-axis                  | `flex-start`, `center`                    |
| flex-wrap       | Wraps elements to the next line         | `wrap`, `wrap-reverse`                    |

#### The Flex Container

Let's make the li's flex items by adding the following code.

```css
nav.ListContainer ul {
	display: flex;
}
```

Now the elements are aligned horizontally.

<img src="https://i.imgur.com/woSXdGI.png" width=800/>

#### Flex Wrap

The elements shouldn't all be on the same line so let's see if we can partially fix that with `flex-wrap`

```css
nav.ListContainer ul{
  display: flex;
  flex-wrap: wrap;
}
```

The elements do indeed wrap around now leaving free space in the ul.

<img src="https://i.imgur.com/0XnhLUK.png" width=500/>

#### Space Around

Let's also take advantage of that free space on the right and divy it on all sides of the li's using `justify-content:around`

```css
nav.ListContainer ul {
	display: flex;
	flex-wrap: wrap;
	justify-content: space-around;
}
```

<img src="https://i.imgur.com/gwFH7Ej.png" width=500/>

#### The Flex Children

The main properties that are specific to `flex` children are:

| Property    | What's It Do?                                       | Examples                     |
| ----------- | --------------------------------------------------- | ---------------------------- |
| flex-grow   | Element will grow                                   | `flex-grow: 1`               |
| flex-shrink | Element will shrink                                 | `flex-shrink: 1`             |
| flex-basis  | Default size of an element before space distributed | `flex-basis: 100px`          |
| flex        | Shorthand for the above 3                           | `flex:1` ,`flex: 1 0 100px`, |
| align-self  | Default alignment                                   | `align-self:center`          |
| order  | Reorder the elements                                | `order:1`          |

For this design each li will have a defined width. Let's use the `flex` shorthand property.

```css
li.ItemContainer {
	flex: 1;
}
```

<img src="https://i.imgur.com/4dr734f.png" width=500/>

It almost seems like were back to the original layout. If we include flex-grow and flex-basis we can get closer to the design.

```css
li.ItemContainer {
	flex: 1 0 185px;
}
```

<img src="https://i.imgur.com/suEtHkd.png" width=500/>

It looks good however if we `decrease` the width of the page we can see that the last 2 elements increase in width.

<img src="https://i.imgur.com/DHfrbFa.png" width=500/>

Sometimes thats what you want and it's good to know that this is a possibility however that doesn't fit our design so let's constrain the width of the elements and assign a `max-width`.

```css
li.ItemContainer {
	flex: 1 0 185px;
	max-width: 185px;
}
```

Were almost at our final design. Let's remove the borders and see where we stand.

<img src="https://i.imgur.com/VhKBva3.png" width=500/>

#### Margin or Padding

So it seems like the elements lost some space vertically between them. could use some space between them in all directions. Margin is usually the way to go so let's try that.

```css
li.ItemContainer {
	flex: 1 0 185px;
	max-width: 185px;
	margin: 20px;
}
```

<img src="https://i.imgur.com/XPyMklL.png" width=500/>

Although this creates space we no longer have the items display in 2 rows with 4 elements per row. That is because margin adds to the space occupied by the element but flexbox doesn't take margin into consideration.

Another option to create the illusion of space is to remote margin and add padding.

```css
li.ItemContainer {
	flex: 1 0 185px;
	max-width: 185px;
	padding: 20px;
}
```

That is much better however the last items heading text wraps to the next line.

<img src="https://i.imgur.com/9L01dbm.png" width=500/>

We can fix that by increasing the `max-width` a bit.

```css
li.ItemContainer {
	flex: 1 0 185px;
	max-width: 195px;
	padding: 20px;
}
```

And that completes the design

<img src="https://i.imgur.com/k3P6foE.png" width=500/>

### Bonus: Reordering Elements

There might be a need one day to rearrange the elements in a different order.  Flexbox provides the `order` property for just that reason.  

Let's move `Wedding Vision` element to the end.  

```css
.ListContainer li:first-of-type {
	order: 1
}
```

The order is only applied after all other non-ordered elements are in place.  

<img src="https://i.imgur.com/k228f4p.png" width=500/>

Let's now move `Wedding Websites` to the end as well.  For that we need to target the 2nd li in the list as CSS isn't aware that elements are being moved around. 


```css
.ListContainer li:nth-of-type(2) {
	order: 2
}
```

<img src="https://i.imgur.com/4cmGi3i.png" width=500/>