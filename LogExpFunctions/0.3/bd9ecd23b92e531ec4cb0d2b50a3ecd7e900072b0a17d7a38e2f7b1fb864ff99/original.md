```julia
xexpy(x, y)

```

Return `x * exp(y)` for `y > -Inf`, or zero if `y == -Inf` or if `x == 0` and `y` is finite.

```jldoctest
julia> xexpy(1.0, -Inf)
0.0
```
