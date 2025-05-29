```
quiver3(x, y, z, u, v, w[, spec; kwargs...])
```

Draw a three-dimensional vector field at points `(x,y,z)` with arrows of size `(u,v,w)`.

The style and color of the arrow lines and – optionally – the markers drawn at the `(x,y,z)` points can be configured through the format string `spec` and keyword arguments, as in [`plot`](@ref) and other functions.

Use the keyword argument `arrowscale` to give a scale factor for the size of the arrows.

!!! note
    Unlike in the case of 2d [`quiver`](@ref) plots, the 3-D arrows of `quiver3` do not have heads.


# Examples

```julia
# Create example data
x = repeat(LinRange(-2, 2, 20), inner=10)
y = repeat(LinRange(0, pi, 10), outer=20)
z = sin.(x) .+ cos.(y)
u = 0.1ones(200)
v = zeros(200)
w = 0.5z
# Plot vectors
quiver3(x, y, z, u, v, w, "o", markersize=0.5)

```
