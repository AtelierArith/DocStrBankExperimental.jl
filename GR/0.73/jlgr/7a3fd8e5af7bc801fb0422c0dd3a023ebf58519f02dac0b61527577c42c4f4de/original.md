Draw one or more three-dimensional line plots.

:param x: the x coordinates to plot :param y: the y coordinates to plot :param z: the z coordinates to plot

**Usage examples:**

.. code-block:: julia

```
julia> # Create example data
julia> x = LinRange(0, 30, 1000)
julia> y = cos.(x) .* x
julia> z = sin.(x) .* x
julia> # Plot the points
julia> plot3(x, y, z)
```
