Draw a stem plot.

This function can receive one or more of the following:

  * x values and y values, or
  * x values and a callable to determine y values, or
  * y values only, with their indices as x values

:param args: the data to plot

**Usage examples:**

.. code-block:: julia

```
julia> # Create example data
julia> x = LinRange(-2, 2, 40)
julia> y = 0.2 .* x .+ 0.4
julia> # Plot x and y
julia> stem(x, y)
julia> # Plot x and a callable
julia> stem(x, x -> x^3 + x^2 + x + 6)
julia> # Plot y, using its indices for the x values
julia> stem(y)
```
