```
isolines(xs::Vector{Float64}, ys::Vector{Float64}, zs::Matrix{Float64}, values::Vector{Float64})
```

Create a vector of isolines from the matrix `zs` for all `values`. The rows of `zs` correspond to the linear spaced values in `ys` and the columns to `xs`. Each entry of the return vector is a NamedTuple with two Vector{Float64} fields `x` and `y`, and the Vector{Int} field `id`. Each unique id marks one line.
