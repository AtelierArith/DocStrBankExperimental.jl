Redraw current plot

This can be used to update the current plot, after setting some attributes like the title, axes labels, legend, etc.

**Usage examples:**

.. code-block:: julia-repl

```
julia> # Create example data
julia> x = LinRange(-2, 2, 40)
julia> y = 2 .* x .+ 4
julia> # Add title and labels
julia> title("Example plot")
julia> xlabel("x")
julia> ylabel("y")
julia> # Redraw the plot with the new attributes
julia> redraw()
```
