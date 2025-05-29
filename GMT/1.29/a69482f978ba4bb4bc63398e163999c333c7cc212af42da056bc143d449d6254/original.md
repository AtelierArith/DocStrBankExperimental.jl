```
texture_img(G::GMTgrid; detail=1.0, contrast=2.0, intensity=false)
```

Compute the Texture Shading calling functions from the software from Leland Brown at http://www.textureshading.com/Home.html

  * `G`: The $GMTgrid$ from which to compute the Leland texture illumination image.
  * `detail` is the amount of texture detail. Lower values of detail retain more elevation information, giving more sense of the overall, large structures and elevation trends in the terrain, at the expense of fine texture detail. Higher detail enhances the texture but gives an overall "flatter" general appearance, with elevation changes and large structure less apparent.
  * `contrast` is a parameter called “vertical enhancement.” Higher numbers increase contrast in the midtones, but may lose detail in the lightest and darkest features. Lower numbers highlight only the sharpest ridges and deepest canyons but reduce contrast overall.
  * `intensity | uint16` controls if output is a UInt16 or a UInt8 image (the default). Note that the original code writes only UInt16 images but if we want to combine this with the hillshade computed with $gdaldem$, a UInt8 image is more handy.

### Returns

A UInt8 (or 16) GMT Image
