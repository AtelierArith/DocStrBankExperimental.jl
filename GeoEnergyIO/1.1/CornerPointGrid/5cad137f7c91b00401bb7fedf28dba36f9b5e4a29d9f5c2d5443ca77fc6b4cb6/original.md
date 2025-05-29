```
cpgrid_from_horizons(X, Y, depths)
cpgrid_from_horizons(X, Y, depths, (100, 100))
cpgrid_from_horizons(X, Y, depths, sz = missing;
    layer_width = 1,
    transforms = [(x, y, z, x_c, y_c, i, j, k) -> z],
    xy_transform = (x, y, i, j, z_t, z_b) -> (x, y, x, y)
)
```

Create a CornerPointGrid from a set of horizons. The horizons are given as a set of 2D arrays, where each array represents the depth of a horizon at each point in the grid. The horizons must be the same size and will be used to create the top and bottom of each cell in the grid. At least two horizons must be provided, one for the top and one for the bottom of the grid, and additional horizons can be provided. If horizons intersect, the cells will be pinched so that the lowest horizon is preserved.

The grid will be created with the given `X` and `Y` coordinates which are vectors/ranges of equal length to the number of rows and columns in the depths arrays. The `sz` argument can be used to resample the grid to a different size in the I/J directions. If `sz` is not provided, the grid will have the same size as the horizons.

# Keyword arguments

  * `layer_width`: Number of cells inside each layer. Can be a single integer or an array of integers with the same length as the number of horizons/depths minus one. Default is 1, i.e. that each layer has one cell in the vertical direction.
  * `transforms`: A function or an array of functions that can be used to modify the depth of each cell. The function(s) should take the following arguments: `x`, `y`, `z`, `x_c`, `y_c`, `i`, `j`, `k`, where `x`, `y` and `z` are the coordinates of the point to be modified, `x_c` and `y_c` are the coordinates of the cell center that the point belongs to, `i` and `j` are the indices of the cell in the I/J directions, and `k` is the index of the cell in the K direction. The function(s) should return the new depth of the point.
  * `xy_transform`: A function that can be used to modify the X and Y coordinates of each pillar. The function should take the following arguments: `x`, `y`, `i`, `j`, `z_t`, `z_b`, where `x` and `y` are the original X and Y coordinates of the line, `i` and `j` are the indices of the line in the I/J directions, and `z_t` and `z_b` are the top and bottom depths of the line. The function should return the new X and Y coordinates of the line.
