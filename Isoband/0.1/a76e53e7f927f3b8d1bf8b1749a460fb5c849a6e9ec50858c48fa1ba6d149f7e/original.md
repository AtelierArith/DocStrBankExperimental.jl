```
isobands(xs, ys, zs, low::Real, high::Real)
```

Create one isoband from the matrix `zs` for the boundaries `low` and `high`. The rows of `zs` correspond to the linear spaced values in `ys` and the columns to `xs`. Returns a NamedTuple with two Vector{Float64} fields `x` and `y`, and the Vector{Int} field `id`. Each unique id marks one polygon, the polygons can be outer polygons or holes and are given in no particular order. Therefore, they must probably be post-processed to feed them to plotting packages.
