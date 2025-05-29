```
cellarray(xmin::Real, xmax::Real, ymin::Real, ymax::Real, dimx::Int, dimy::Int, color)
```

Display rasterlike images in a device-independent manner. The cell array function partitions a rectangle given by two corner points into DIMX X DIMY cells, each of them colored individually by the corresponding color index of the given cell array.

**Parameters:**

`xmin`, `ymin` :     Lower left point of the rectangle `xmax`, `ymax` :     Upper right point of the rectangle `dimx`, `dimy` :     X and Y dimension of the color index array `color` :     Color index array

The values for `xmin`, `xmax`, `ymin` and `ymax` are in world coordinates.
