```julia
xexpx(x)

```

Return `x * exp(x)` for `x > -Inf`, or zero if `x == -Inf`.

```jldoctest
julia> xexpx(-Inf)
0.0
```
