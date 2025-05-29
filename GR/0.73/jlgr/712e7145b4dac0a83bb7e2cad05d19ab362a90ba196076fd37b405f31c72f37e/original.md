Draw a heatmap.

This function uses the current colormap to display a two-dimensional array as a heatmap. The array is drawn with its first value in the bottom left corner, so in some cases it may be neccessary to flip the columns (see the example below).

By default the function will use the column and row indices for the x- and y-axes, respectively, so setting the axis limits is recommended. Also note that the values in the array must lie within the current z-axis limits so it may be neccessary to adjust these limits or clip the range of array values.

:param data: the heatmap data

**Usage examples:**

.. code-block:: julia

```
julia> # Create example data
julia> x = LinRange(-2, 2, 40)
julia> y = LinRange(0, pi, 20)
julia> z = sin.(x') .+ cos.(y)
julia> # Draw the heatmap
julia> heatmap(z)
```
