```
grayscale(R [, bwcode]; width::Int, height::Int, exactsize=false)
```

Transform the recurrence matrix `R` into a full matrix suitable for plotting as a grayscale image. By default it returns a matrix with the same size as `R`, but switched axes, containing "black" values in the cells that represent recurrent points, and "white" values in the empty cells and interpolating in-between for cases with both recurrent and empty cells, see below.

The numeric codes for black and white are given in a 2-element tuple as a second optional argument. Its default value is `(0.0, 1.0)`, i.e. black is coded as `0.0` (no brightness) and white as `1.0` (full brightness). The type of the elements in the tuple defines the type of the returned matrix. This must be taken into account if, for instance, the image is coded as a matrix of integers corresponding to a grayscale; in such case the black and white codes must be given as numbers of the required integer type.

The keyword arguments `width` and `height` can be given to define a custom size of the image. If only one dimension is given, the other is automatically calculated. If both dimensions are given, by default they are adjusted to keep an aspect proportional to the original matrix, such that the returned matrix fits into a matrix of the given dimensions. This automatic adjustment can be disabled by passing the keyword argument `exactsize=true`.

If the image has different dimensions than `R`, the cells of `R` are distributed in a grid with the size of the image, and a gray level between white and black is calculated for each element of the grid, proportional to the number of recurrent points contained in it. The levels of gray are coded as numbers of the same type as the black and white codes.

It is advised to use `width, height` arguments for large matrices otherwise plots using functions like e.g. `heatmap` could be misleading.
