```
isolines(xs, ys, zs, value::Real)
```

Create one isoline from the matrix `zs` for `value`. The rows of `zs` correspond to the linear spaced values in `ys` and the columns to `xs`. Returns a NamedTuple with two Vector{Float64} fields `x` and `y`, and the Vector{Int} field `id`. Each unique id marks one line.
