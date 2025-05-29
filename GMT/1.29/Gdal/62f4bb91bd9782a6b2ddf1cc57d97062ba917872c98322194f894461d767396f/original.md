```
dither(indata; n_colors=256, save="", gdataset=false)
```

Convert a 24bit RGB image to 8bit paletted.

  * Use the `save=fname` option to save the result to disk in a GeoTiff file `fname`. If `fname` has no extension a `.tif` one will be appended. Alternatively give file names with extension `.png` or `.nc` to save the file in one of those formats.
  * `gdataset=true`: to return a GDAL dataset. The default is to return a GMTimage object.
  * `n_colors`: Select the number of colors in the generated color table. Defaults to 256.
