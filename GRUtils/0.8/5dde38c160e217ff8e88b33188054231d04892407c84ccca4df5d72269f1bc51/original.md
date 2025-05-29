```
isosurface(data, isovalue; kwargs...)
```

Draw an isosurface determined by the region of the three-dimensional array `data` around a given `isovalue`.

The isosurface is calculated so that values in `data` greater than `isovalue` are considered to be outside the surface, and the values lower than `isovalue` are inside the surface.

The color of the isosurface can be chosen with the keyword argument `color`, with the hexadecimal RGB color code.

# Examples

```julia
# Create example data
s = LinRange(-4, 4, 50)
v = cos.(s) .+ cos.(s)' .+ cos.(reshape(s,1,1,:))
# Draw the isosurface
isosurface(v, 0.5, color=0x99ffcc)

```
