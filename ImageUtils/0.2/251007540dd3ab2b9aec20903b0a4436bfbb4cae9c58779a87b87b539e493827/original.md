```
exportMovie(filename, data, colorm; vmin, vmax, normalize, pixelResizeFactor)
```

Exports video-data (threedimensional Colorant Array) `data` as `filename` (path) colored with the colormap `colorm` (default: grays).

Colormaps can be given directly as a Vector of Colorants. Alternatively a colormap from ColorSchemes (with added alpha gradient from 0 to 1) can be used by giving a String with the name of the colormap. All existing colormaps can be found using `existing_cmaps()`. Frequently used colormaps can be found using `important_cmaps()`. Colormaps with customized alpha gradients can be build using `RGBAGradient()`.

Further keyword arguments:

  * `vmin` and `vmax` (default: 0.0 and 1.0): floating numbers, left and right limits for coloring
  * `normalize` (default: true): boolean, normalize data to [0,1] if true
  * `pixelResizeFactor` (default: 1): integer number, amount of multiple pixels plotted for each datapoint
