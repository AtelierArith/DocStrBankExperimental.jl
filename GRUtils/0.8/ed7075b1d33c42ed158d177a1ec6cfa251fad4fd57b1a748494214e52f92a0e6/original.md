```
quiver(x, y, u, v[, spec; kwargs...])
```

Draw a vector field at points `(x,y)` with arrows of size `(u,v)`.

The style and color of the arrow lines and – optionally – the markers drawn at the `(x,y)` points can be configured through the format string `spec` and keyword arguments, as in [`plot`](@ref) and other functions.

Use the keyword arguments `arrowscale` and `headsize` to give a scale factor for the size of the arrows and their heads.

# Examples

```julia
# Create example data
x = repeat(LinRange(-2, 2, 20), inner=10)
y = repeat(LinRange(-1, 1, 10), outer=20)
u = x .* (x.^2 .+ y.^2)
v = y .* (x.^2 .+ y.^2)
# Plot arrows
quiver(x, y, u, y, arrowscale=0.1)
# Expand the y-axes to see the whole arrows
ylim(-1.15, 1.15)

```
