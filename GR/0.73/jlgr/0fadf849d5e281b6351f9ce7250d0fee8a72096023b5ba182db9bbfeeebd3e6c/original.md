Set the hold flag for combining multiple plots.

The hold flag prevents drawing of axes and clearing of previous plots, so that the next plot will be drawn on top of the previous one.

:param flag: the value of the hold flag

**Usage examples:**

.. code-block:: julia

```
julia> # Create example data
julia> x = LinRange(0, 1, 100)
julia> # Draw the first plot
julia> plot(x, x.^2)
julia> # Set the hold flag
julia> hold(true)
julia> # Draw additional plots
julia> plot(x, x.^4)
julia> plot(x, x.^8)
julia> # Reset the hold flag
julia> hold(false)
```
