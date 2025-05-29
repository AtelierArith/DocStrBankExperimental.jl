```
polarheatmap(data; kwargs...)
```

Draw a polar heatmap

The current colormap is used to display a two-dimensional array `data` as a polar heatmap.

If `data` is an *N*×*M* array, the cells of the matrix will be plotted in a circle divided in *M* angular sectors and *N* rings, such that the values of the first row will be concentrated in the center of the circle, and the following rows will be drawn in increasing concentric rings. The columns of the array are drawn as radii of the circle in a counterclockwise order, starting and ending in horizontal axis pointing to the right.

# Examples

```julia
# Create example data
angle = LinRange(0, 2π, 40)
radius = LinRange(0, 10, 20)
z = sin.(angle') .* cos.(radius)
polarheatmap(z)

```
