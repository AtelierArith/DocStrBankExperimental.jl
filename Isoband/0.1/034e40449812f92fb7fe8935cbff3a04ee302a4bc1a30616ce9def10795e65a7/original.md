```
isobands(xs::Vector{Float64}, ys::Vector{Float64}, zs::Matrix{Float64}, low_values::Vector{Float64}, high_values::Vector{Float64})
```

Create a vector of isobands from the matrix `zs` for all pairs in `low_values` and `high_values`. The rows of `zs` correspond to the linear spaced values in `ys` and the columns to `xs`. Each entry of the return vector is a NamedTuple with two Vector{Float64} fields `x` and `y`, and the Vector{Int} field `id`. Each unique id marks one polygon, the polygons can be outer polygons or holes and are given in no particular order. Therefore, they must probably be post-processed to feed them to plotting packages.
