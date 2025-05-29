```
nonuniformpolarcellarray(x, y, dimx::Int, dimy::Int, color)
```

Display a two dimensional color index array mapped to a disk using nonuniform polar coordinates.

**Parameters:**

`x`, `y` :     X and Y coordinates of the cell edges `dimx`, `dimy` :     X and Y dimension of the color index array `color` :     Color index array

The two dimensional color index array is mapped to the resulting image by interpreting the X-axis of the array as the angle and the Y-axis as the radius.
