```
surface([x, y,] z; kwargs...)
```

Draw a three-dimensional surface plot.

Either a series of points or a two-dimensional array is drawn as a surface plot, colored according to the Z coordinates and the current colormap. It can receive one of the following:

  * `x` values, `y` values and `z` values.
  * *M* sorted values of the `x` axis, *N* sorted values of the `y` axis,   and a set of `z` values on a *N*×*M* grid.
  * *M* sorted values of the `x` axis, *N* sorted values of the `y` axis,   and a callable to determine `z` values.
  * `z` values on a *N*×*M* grid, with the *x* and *y* axes   defined as the indices of the columns and rows of the grid, respectively.

If a series of points is passed to this function, their values will be interpolated on a grid. For grid points outside the convex hull of the provided points, a value of 0 will be used.

# Examples

```julia
# Create example grid data
x = LinRange(-2, 2, 40)
y = LinRange(0, pi, 20)
z = sin.(x') .+ cos.(y)
# Surface plot
surface(x, y, z)

```
