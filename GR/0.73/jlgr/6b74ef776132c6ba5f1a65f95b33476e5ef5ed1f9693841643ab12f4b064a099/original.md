Draw one or more scatter plots.

This function can receive one or more of the following:

  * x values and y values, or
  * x values and a callable to determine y values, or
  * y values only, with their indices as x values

Additional to x and y values, you can provide values for the markers' size and color. Size values will determine the marker size in percent of the regular size, and color values will be used in combination with the current colormap.

:param args: the data to plot

**Usage examples:**

.. code-block:: julia

```
julia> # Create example data
julia> x = LinRange(-2, 2, 40)
julia> y = 0.2 .* x .+ 0.4
julia> # Plot x and y
julia> scatter(x, y)
julia> # Plot x and a callable
julia> scatter(x, x -> 0.2 * x + 0.4)
julia> # Plot y, using its indices for the x values
julia> scatter(y)
julia> # Plot a diagonal with increasing size and color
julia> x = LinRange(0, 1, 11)
julia> y = LinRange(0, 1, 11)
julia> s = LinRange(50, 400, 11)
julia> c = LinRange(0, 255, 11)
julia> scatter(x, y, s, c)
```
