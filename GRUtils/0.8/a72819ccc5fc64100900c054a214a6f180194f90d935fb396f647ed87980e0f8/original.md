```
radians(flag::Bool)
```

Set the scale of angles in polar plots.

Use `radians(true)` to represent angles in radians (default setting), and `radians(false)` to represent them in degrees.

This operation only modifies the guides of the polar plot grid lines. The existing geometries are left without changes

Use the keyword argument `radians=<true/false>`, etc. in plotting functions, to set the scale of angles during the creation of polar plots.

# Example

```julia
# Example data
θ = LinRange(0, 2π, 40)
r = sin.(θ)
# Draw the polar plot (by default in radians)
polar(θ, r)
# Change the angula scale
radians(false)
```
