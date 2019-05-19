# responsive-images

This sample project helps us understand img tag's srcset and sizes attributes. Suppose your app has resized an image into the following sizes 400px, 800px, 1200px and 1600px, then the code below will serve the particular version of your image based on client's viewport size and screen density.

```html
<img src="img/autum-800.jpg"
     srcset="img/autum-400.jpg 400w,
             img/autum-800.jpg 800w,
             img/autum-1200.jpg 2x,
             img/autum-1600.jpg 3x"
     sizes="(max-width: 800px) 100vw, 1200px"
     alt="autum">
```

The above img tag renders an 800px image by default, but depending on the client's viewport size and screen density, it actually may serve the 400px, 800px, 1200px or 1600px version of the image.

The `sizes="(max-width: 800px) 100vw, 1200px"` attribute says if client viewport size is <= 800px then let the viewport decide 100%, otherwise use 1200px.  In other words, it is basically saying when _client screen density is 1x_, and when client's viewport size is <= 400px, use the 400px image; if viewport size is <= 800px, use the 800px image; in all other cases use 1200px image. It is equivalent to `sizes="(max-width: 400px) 400px, (max-width: 800px) 800px, 1200px"`.

However, regardless of client's viewport size, when client density is between 1x and 2x, i.e. > 1x && <=2x, the 1200px image will be served; when it is greater than 2x, the 1600px image is served.

To see this happen in action, do the following.

1. Launch index.html with FireFox (Chrome has a caching issue by design).
2. Press Ctrl+Shift+M to open Responsive Design Mode.
3. Drag the bottom right corner to resize the displayed area to be

    * below 400px
    * between 400px and 800px
    * between 800px and 1200px
    * greater than 1200px

4. Then try change DPR (1,2,3) while adjusting area to above listed sizes.
5. Finally try click on Responsive dropdown to test different devices from phones, tablets to laptops.
6. Also check out index2.html and index3.html for cases where you have fewer resized images.

## Resources

* [Mozilla Web Docs on Responsive images](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)
* [Best Screen Size to Design for 2019](https://www.hobo-web.co.uk/best-screen-size/)
* [Understand Density Pixel Ratio](https://youtu.be/2QYpkrX2N48?t=179)
