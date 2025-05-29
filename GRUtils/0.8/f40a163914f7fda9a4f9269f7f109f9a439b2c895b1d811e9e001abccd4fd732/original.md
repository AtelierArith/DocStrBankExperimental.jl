```
wireframe([x, y,] z; kwargs...)
```

Draw a three-dimensional wireframe plot.

Either a series of points or a two-dimensional array is drawn as a wireframe plot. It can receive one of the following:

  * `x` values, `y` values and `z` values.
  * *M* sorted values of the `x` axis, *N* sorted values of the `y` axis,   and a set of `z` values on a *N*×*M* grid.
  * *M* sorted values of the `x` axis, *N* sorted values of the `y` axis,   and a callable to determine `z` values.
  * `z` values on a *N*×*M* grid, with the *x* and *y* axes   defined as the indices of the columns and rows of the grid, respectively.

Also use the attributes `color` and `linecolor` to set the color of the surface and lines of the mesh, as RGB hexadecimal color values.

If a series of points is passed to this function, their values will be interpolated on a grid. For grid points outside the convex hull of the provided points, a value of 0 will be used.

# Examples

```julia
# Create example grid data
x = LinRange(-2, 2, 40)
y = LinRange(0, pi, 20)
z = sin.(x') .+ cos.(y)
# Wireframe plot
wireframe(x, y, z)

```
