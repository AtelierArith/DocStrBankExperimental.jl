Draw one or more line plots.

This function can receive one or more of the following:

  * x values and y values, or
  * x values and a callable to determine y values, or
  * y values only, with their indices as x values

:param args: the data to plot

**Usage examples:**

.. code-block:: julia-repl

```
julia> # Create example data
julia> x = LinRange(-2, 2, 40)
julia> y = 2 .* x .+ 4
julia> # Plot x and y
julia> plot(x, y)
julia> # Plot x and a callable
julia> plot(x, t -> t^3 + t^2 + t)
julia> # Plot y, using its indices for the x values
julia> plot(y)
```
