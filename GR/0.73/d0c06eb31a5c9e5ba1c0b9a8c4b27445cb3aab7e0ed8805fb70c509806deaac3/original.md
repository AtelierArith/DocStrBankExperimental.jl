```
nonuniformcellarray(x, y, dimx::Int, dimy::Int, color)
```

Display a two dimensional color index array with nonuniform cell sizes.

**Parameters:**

`x`, `y` :     X and Y coordinates of the cell edges `dimx`, `dimy` :     X and Y dimension of the color index array `color` :     Color index array

The values for `x` and `y` are in world coordinates. `x` must contain `dimx` + 1 elements and `y` must contain `dimy` + 1 elements. The elements i and i+1 are respectively the edges of the i-th cell in X and Y direction.
