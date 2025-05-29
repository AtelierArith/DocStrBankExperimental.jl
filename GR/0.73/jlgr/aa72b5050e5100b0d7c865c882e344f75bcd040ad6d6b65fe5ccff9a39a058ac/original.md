Draw one or more three-dimensional scatter plots.

Additional to x, y and z values, you can provide values for the markers' color. Color values will be used in combination with the current colormap.

:param x: the x coordinates to plot :param y: the y coordinates to plot :param z: the z coordinates to plot :param c: the optional color values to plot

**Usage examples:**

.. code-block:: julia

```
julia> # Create example data
julia> x = 2 .* rand(100) .- 1
julia> y = 2 .* rand(100) .- 1
julia> z = 2 .* rand(100) .- 1
julia> c = 999 .* rand(100) .+ 1
julia> # Plot the points
julia> scatter3(x, y, z)
julia> # Plot the points with colors
julia> scatter3(x, y, z, c)
```
