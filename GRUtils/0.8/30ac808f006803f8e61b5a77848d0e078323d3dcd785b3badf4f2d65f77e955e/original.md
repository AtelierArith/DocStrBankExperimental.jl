```
heatmap([x, y,] data; kwargs...)
```

Draw a heatmap.

The current colormap is used to display a two-dimensional array `data` as a heatmap.

If `data` is an *N*×*M* array, the cells of the heatmap will be plotted in a grid of rectangular cells, whose edges are defined by the coordinates `x` (a sorted vector with `M+1` values) and `y` (a sorted vector with `N+1` values).

If `x` and `y` are not given, a uniform grid is drawn spanning the interval `[1, M+1]` in the X-axis, and `[1, N+1]` in the Y-axis.

The array is drawn with its first value in the bottom left corner, so in some cases it may be neccessary to flip the axes.

By default column and row indices are used for the x- and y-axes, respectively, so setting the axis limits is recommended. Also note that the values in the array must lie within the current z-axis limits so it may be neccessary to adjust these limits or clip the range of array values.

# Examples

```julia
# Uniform heatmap on the left
subplot(1,2,1)
x = LinRange(-2, 2, 40)
y = LinRange(0, pi, 20)
z = sin.(x') .+ cos.(y)
heatmap(z)
# Non uniform heatmap on the right
subplot(1,2,2)
x = [0, 2, 3, 4.5, 5]
y = [2, 3, 4.5, 5, 6, 8]
z = rand(5, 4)
heatmap(x, y, z)

```
