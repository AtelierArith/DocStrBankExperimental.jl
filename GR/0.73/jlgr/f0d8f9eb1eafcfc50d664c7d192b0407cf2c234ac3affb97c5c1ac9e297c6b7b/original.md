Draw a triangular contour plot.

This function uses the current colormap to display a series of points as a triangular contour plot. It will use a Delaunay triangulation to interpolate the z values between x and y values. If the series of points is concave, this can lead to interpolation artifacts on the edges of the plot, as the interpolation may occur in very acute triangles.

:param x: the x coordinates to plot :param y: the y coordinates to plot :param z: the z coordinates to plot

**Usage examples:**

.. code-block:: julia

```
julia> # Create example point data
julia> x = 8 .* rand(100) .- 4
julia> y = 8 .* rand(100) .- 4
julia> z = sin.(x) + cos.(y)
julia> # Draw the triangular contour plot
julia> tricont(x, y, z)
```
