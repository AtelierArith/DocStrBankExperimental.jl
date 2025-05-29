```
blendimg!(color::GMTimage, shade::GMTimage; new=false, mode="", transparency=0.5, white=220, burn_up=180, screen_low=200)
```

Blend `color` GMTimage that is normally a RGB image with the `shade` intensity image (normally obtained with gdaldem or Blender ray tracer). However, for certain blender modes both $color$ or $shade$ can be RGB or grayscale images. It is highly instructive to watch this YouTube video on how to combine the "LinearBurn" and the "Screen" modes to create stunning "Shaded relief" effects. https://somethingaboutmaps.wordpress.com/2014/10/26/adding-shaded-relief-in-photoshop/

  * `mode`:

      * `mode=""` or `mode="gcalc"`: The blending method is the one explained at https://gis.stackexchange.com/questions/255537/merging-hillshade-dem-data-into-color-relief-single-geotiff-with-qgis-and-gdal/255574#255574
      * `mode="blend"`: Simple 50% (default) blend is performed. Set `transparency` to other value in the ]0 1[ range to weight more one of the images. 0.75 will make `img` weight 3/4 of the total sum, and so forth.
      * `mode="LinearBurn"`: (Same as Photoshop blender *LinearBurn*) Adds the pixel values of the upper and lower layers and then subtracts 255. It tends to make the image darker. The `burn_up` option sets the threshold value of $shade$ above which the $color$ image is not modified.
      * `mode="ColorBurn"`: (Same as Photoshop blender *ColorBurn*) It inverts the pixel value of $color$ layer, divides that by the pixel value of the $shade$, then inverts the result. It tends to make the image darker.
      * `mode="Screen"`: (Same as Photoshop blender *Screen*) Inverts the values of each of the visible pixels in the two images. (That is, it subtracts each of them from 255) Then it multiplies them together, and inverts this value again. The resulting image is usually brighter, and sometimes “washed out” in appearance. To control this washing effect, use the `screen_low` option that sets the threshold value of $shade$ below which the $color$ image is not modified. Note, this value is very case dependent and normally requires some trial and error to find the right value. A second way of controlling the washing effect is to use the `white` option different from 255. The default here is `white=220` which makes the added bright be less bright.
  * `new`: If true returns a new GMTimage object, otherwise it changes the `color` content.
