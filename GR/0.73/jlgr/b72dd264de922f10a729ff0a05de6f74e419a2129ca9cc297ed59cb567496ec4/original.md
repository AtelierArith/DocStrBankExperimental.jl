Draw a hexagon binning plot.

This function uses hexagonal binning and the the current colormap to display a series of points. It  can receive one or more of the following:

  * x values and y values, or
  * x values and a callable to determine y values, or
  * y values only, with their indices as x values

:param args: the data to plot

**Usage examples:**

.. code-block:: julia

```
julia> # Create example data
julia> x = randn(100000)
julia> y = randn(100000)
julia> # Draw the hexbin plot
julia> hexbin(x, y)
```
