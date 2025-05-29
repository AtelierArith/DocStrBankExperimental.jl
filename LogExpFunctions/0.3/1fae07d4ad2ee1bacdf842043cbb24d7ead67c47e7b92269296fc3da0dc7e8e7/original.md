```julia
xlogx(x)

```

Return `x * log(x)` for `x ≥ 0`, handling $x = 0$ by taking the downward limit.

```jldoctest
julia> xlogx(0)
0.0
```
