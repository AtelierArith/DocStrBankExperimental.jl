```
[I = ] lelandshade(G::GMTgrid; detail=1.0, contrast=2.0, intensity=false, zfactor=3, transparency=0.6,
                   show=false, color=false, opts=String[], cmap="", kw...)
```

Compute a grayscale or color shaded illumination image using the thechnique developed by [Leland Brown's "texture shading"](http://www.textureshading.com/Home.html) 

  * `G`: A $GMTgrid$ or a grid file name from which to compute the Leland texture illumination image.
  * `detail` is the amount of texture detail. Lower values of detail retain more elevation information, giving more sense of the overall, large structures and elevation trends in the terrain, at the expense of fine texture detail. Higher detail enhances the texture but gives an overall "flatter" general appearance, with elevation changes and large structure less apparent.
  * `contrast` is a parameter called “vertical enhancement.” Higher numbers increase contrast in the midtones, but may lose detail in the lightest and darkest features. Lower numbers highlight only the sharpest ridges and deepest canyons but reduce contrast overall.
  * `intensity | uint16` controls if output is a UInt16 or a UInt8 image (the default). Note that the original code writes only UInt16 images but if we want to combine this with the hillshade computed with $gdaldem$, a UInt8 image is more handy.
  * `zfactor`: A terrain amplification factor used in $gdaldem$ when computing the "hillshade"
  * `transparency`: The transparency of the texture image computed with the Leland algorithm when blended with hillshade computed with $gdaldem$. The default value, 0.5, gives equal weight to both images. A value of 0.75 will make the texture image weight 3/4 of the total sum, and so forth.
  * `color`: Boolean that selects if the output is a color or a grayscale image (the default). For color images we create a default linear color map (via a call to $makecpt$), but this can be overruled with the `cmap` option.
  * `equalize`: For color images one may select to histogram equalize the colors (via a call to $grd2cpt$). This option alone (as well as `cmap`) also sets `color=true`.
  * `opts`: A (optional) string vector with $gdaldem$ dedicated options (see its man mage). Use this to fine tune the "hillshade" part of the final image.
  * `cmap`: When doing color images and don't want the default cmap, pass a color map (cpt) name (file or master cpt name) or $GMTcpt$. This also sets `color=true`.
  * `colorbar`: Boolean, used only when `show=true`, to add a colorbar on the right side of the image.
  * `show`: Boolean that if set to `true` will show the result immediately. If `false`, a $GMTimage$ object is returned.
  * `kw`: The keword/value pairs that can be used to pass arguments to $makecpt$, $grd2cpt$ and $gdaldem$.

### Examples:

```
lelandshade(gmtread("@earth_relief_01s", region=(-114,-113,35,36)), color=true, colorbar=true, show=true)
```

### Returns

A GMTimage object (8 or 16 bits depending on the `intensity` option) if show == false, or nothing otherwise.
