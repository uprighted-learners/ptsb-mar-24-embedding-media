# Embedding Media

Embedding is the process of including *media* from other sources into your web sites.

"other documents" can include:

  * media files
    * images, sound, video
  * other HTML (pages or snippets)
  * advertisements
  * maps, graphs, charts
  * search box e.g. [Google custom search](https://cse.google.com/)

"embedding" is sometimes also called "including" or "transcluding"

---

# Interactive Embedding

Sometimes you can use JavaScript to interact with the embedded file or app as if it were another User Interface element on your page!

For instance, you could programmatically pause and play an embedded audio clip, say, playing "hoorah!" when the user wins a game of Tic-Tac-Toe.

Or, if the user moves their location on an embedded Google Map, your app could be notified and find the city name and look up restaurants in that area on [Yelp's API](https://www.yelp.com/developers/documentation/v3).

> This lesson focuses on *static* embedding:
> displaying media and allowing the user to interact with it directly.
> The [Interactive Embedding](/lessons/week-4/embedding) lesson focuses on *interactive* embedding:
> using JavaScript to pass messages between your page's
> scripts and the embedded media.

---

# Embedding Images

`<img src=''>` is the original embed

[MDN: img](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img)

---

# Where does the media come from?

* Usually images are served from the same web server as HTML.
* Some web sites host images or other media for free or a small cost
  * *images*: flickr.com, imgur.com, 500px.com, etc.
  * *video*: YouTube.com, Vimeo.com, Wistia.com, etc.
  * *audio*: SoundCloud.com, etc.
* a [CDN](https://en.wikipedia.org/wiki/Content_delivery_network#Notable_content_delivery_service_providers) hosts all sorts of media for you for $$$
  * Amazon AWS / CloudFront, CloudFlare, Akamai...

---

# Image Types

There are several different types of images:

* jpg
* png
* svg
* gif
* and many more

The following slides will focus on a few of the common types of images found around the web.

---

# JPEG/JPG

* Common image type
* Small file size
* Lossy compression
* No transparency allowed
* Raster based (pixel) image type
* Rectangular in shape

> Note: JPGs and JPEGs are the same type of image, however when embedding them in your page you will need to make sure you are using the correct file extension otherwise your site won't be able to locate the image.

---

# PNG

* Similar in size to JPGs (though often slightly larger)
* Pixel based (raster) image type
* Supports transparent
* Rectangular in shape

> Note: While PNGs can *appear* to be irregular in shape they are not, transparent sections will still block users from interacting with any content behind them

---

# SVG

SVG stands for **Scalable Vector Graphic**

* Small file size
* Vector based image type
* Scales indefinitely

---

# Embedding IFrames

`<iframe>` means "inline frame"

```html
<iframe 
  id="inlineFrameExample"
  title="Inline Frame Example"
  width="300"
  height="200"
  src="https://www.openstreetmap.org/export/embed.html?bbox=-0.004017949104309083%2C51.47612752641776%2C0.00030577182769775396%2C51.478569861898606&layer=mapnik">
</iframe>
```

**More Information:**

[MDN IFrame Reference](https://www.w3.org/Security/wiki/Same_Origin_Policy)

---

# Malware Vectors

**Beware** the "[same origin policy](https://www.w3.org/Security/wiki/Same_Origin_Policy)":

```
Refused to display 'http://www.burlingtoncodeacademy.com/' in a frame because it set 'X-Frame-Options' to 'sameorigin'.
```

  * Some web servers (e.g. Wordpress) set these headers *on* by default
  * Other web servers (e.g. Apache) set these headers *off* by default

**Beware** giving foreign JavaScript access to your page contents and user-input data

  * the `sandbox` attribute limits what the loaded page can do

---

# Embedding HTML snippets

You can use iframes to load the same HTML onto several pages on your site.

This is often used for login boxes.

> Warning: iframes can take longer to load than the rest of the page, and can eat up CPU and RAM, so don't overuse them

---

# Code Along: Embedding an iFrame

iFrames are often used to embed videos from dedicated hosts such as Vimeo or YouTube

Let's add a video to our hello-html site! Open up YouTube and find a short video, and a long video. Leave them open in different tabs.

* Open up your "hello-html" directory if it's not already open.
* Go back to the open video tabs, and click on the "share" button
  * Choose the "embed" option, and copy the code for the iframe element it gives you
  * Paste that code into your `index.html` file
  * Play around with the options on the iFrame to modify the video's behavior/attributes

---

# Embedding Flash

Adobe Flash has been retired, and is no longer supported. Do not use it.

![R I P Flash](https://res.cloudinary.com/btvca/image/upload/v1574445198/curriculum/rip-flash_gzmwcj.png)

---

# Modern Animations

Flash used allow for web animations, but there are now better options.

* `<canvas>` elements using JavaScript
* Pure CSS animations
* The JavaScript animation API
* Third party animation frameworks such as [Snap SVG](http://snapsvg.io/)

---

# Embedding Video

HTML5 defines a standard `<video>` tag

  * Use the `<video>` tag when you are hosting your own video media file (on your web server or a CDN).
  * Video hosting sites like YouTube, and Vimeo have their own rules and sample code which you should find and copy into your HTML file.

```html
<video controls>
  <source src="myVideo.webm" type="video/webm">
  <source src="myVideo.mp4" type="video/mp4">
  <p>Your browser doesn't support HTML5 video. Here is
     a <a href="myVideo.mp4">link to the video</a> instead.</p>
</video>
```

[MDN Video Tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video) | [MDN Video Tutorial](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content)

---

# Embedding Audio

HTML5 also has a prebuilt `<audio>` tag that you can use to embed your local audio files into your web pages.

* `src` Like with all other forms of media the `src` attribut tells your tag where the actual audio file lives
* `autoplay` Accepts a boolean value, when set to `true` it will begin playback as soon as it can
* `controls` Adding this attribute with no value will display playback controls to the user
* `loop` Another boolean attribute that repeats the audio indefinitely when set to `true`
* `muted` Yet another boolean attribute. It mutes your audio when set to `true`

```html
<audio controls>
  <source src="myAudio.mp3" type="audio/mpeg">
  <source src="myAudio.ogg" type="audio/ogg">
  <p>Your browser doesn't support HTML5 audio. Here is
     a <a href="myAudio.mp3">link to the audio</a> instead.</p>
</audio>
```

[MDN Audio Tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video) | [MDN Audio Tutorial](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content)

---

# Embedding Maps

```html
<iframe id="inlineFrameExample"
  title="Inline Frame Example"
  width="300"
  height="200"
  src="https://www.openstreetmap.org/export/embed.html?bbox=-73.2130900,44.4749000,-73.2102500,44.4772200&layer=mapnik">
</iframe>
```

OpenStreetMaps defines a "bounding box" as a four-tuple: min Longitude, min Latitude, max Longitude, max Latitude.

You can find the bounding box for a given map on https://www.openstreetmap.org/ by clicking the **Export** button.

There are also front end frameworks that make creating, and manipulating embedded maps easier. We will be looking at one of those next week when we dive into client side coding.

---

# Scripting Maps

It is possible to use JavaScript to interact with an embedded map. See [the client-side coding lesson on interactive mapping](/lessons/slides/using-libraries)