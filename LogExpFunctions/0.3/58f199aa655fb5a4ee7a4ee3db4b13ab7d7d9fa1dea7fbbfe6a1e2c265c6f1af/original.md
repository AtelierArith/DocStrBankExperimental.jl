```julia
xlog1py(x, y)

```

Return `x * log(1 + y)` for `y ≥ -1` with correct limit at $x = 0$.

```jldoctest
julia> xlog1py(0, -1)
0.0
```
