Draw one or more line plots over another plot.

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
julia> y = 2 .* x .+ 4
julia> # Draw the first plot
julia> plot(x, y)
julia> # Plot graph over it
julia> oplot(x, x -> x^3 + x^2 + x)
```
