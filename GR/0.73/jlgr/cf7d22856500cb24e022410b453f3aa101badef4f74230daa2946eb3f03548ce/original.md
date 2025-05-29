Draw one or more polar plots.

This function can receive one or more of the following:

  * angle values and radius values, or
  * angle values and a callable to determine radius values

:param args: the data to plot

**Usage examples:**

.. code-block:: julia

```
julia> # Create example data
julia> angles = LinRange(0, 2pi, 40)
julia> radii = LinRange(0, 2, 40)
julia> # Plot angles and radii
julia> polar(angles, radii)
julia> # Plot angles and a callable
julia> polar(angles, r -> cos(r) ^ 2)
```
