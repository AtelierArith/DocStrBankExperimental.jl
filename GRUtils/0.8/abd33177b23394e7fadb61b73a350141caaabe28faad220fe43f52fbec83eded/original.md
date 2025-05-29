```
contourf([x, y,] z; kwargs...)
```

Draw a filled contour plot.

The current colormap is used to display a either a series of points or a two-dimensional array as a filled contour plot. It can receive one of the following:

  * `x` values, `y` values and `z` values.
  * *M* sorted values of the `x` axis, *N* sorted values of the `y` axis,   and a set of `z` values on a *N*×*M* grid.
  * *M* sorted values of the `x` axis, *N* sorted values of the `y` axis,   and a callable to determine `z` values.
  * `z` values on a *N*×*M* grid, with the *x* and *y* axes   defined as the indices of the columns and rows of the grid, respectively.

If a series of points is passed to this function, their values will be interpolated on a grid. For grid points outside the convex hull of the provided points, a value of 0 will be used.

The following keyword arguments can be provided to set the number and aspect of the contour lines:

  * `levels::Int`, the number of contour lines that will be fitted to the data   (20 by default).
  * `majorlevels::Int`, the number of levels between labelled contour lines   (no labels by default).

# Examples

```julia
# 1. Create example point data
x = 8 .* rand(100) .- 4
y = 8 .* rand(100) .- 4
z = sin.(x) + cos.(y)
# Contour plot
contourf(x, y, z)
# 2. Create example grid data with a callable
x = LinRange(-2, 2, 40)
y = LinRange(0, pi, 20)
f(x, y) = sin(x) + cos(y)
# Contour plot with 25 lines, labelling a quarter of them
contourf(x, y, f, levels = 25, majorlevels = 4)

```
