```
polar(angle, radius[, spec; kwargs...])
```

Draw one or more polar plots.

The first coordinate the represents the angle, and the second the radius of the line points. The rest is defined as for line plots, except that the first variable (`angle`) is always required. (cf. [`plot`](@ref)).

The first variable is by default considered to be radians, and the angular labels of the grid are shown as factors of π. Use the keyword argument `radians = false` to pass and show angles in degrees.

!!! note
    Logarithmic and reversed scales ar disabled in polar plots


# Examples

```julia
# Create example data
angles = LinRange(0, 360, 40)
radii = LinRange(0, 2, 40)
# Draw the polar plot in degrees
polar(angles, radii, radians=false)

```
