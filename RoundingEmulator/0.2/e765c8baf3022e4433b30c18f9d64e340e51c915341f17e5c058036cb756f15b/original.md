```
sqrt_up(a)
```

Computes `sqrt(a)` with the rounding mode [`Base.Rounding.RoundUp`](https://docs.julialang.org/en/v1/base/math/#Base.Rounding.RoundUp).

```jldoctest
julia> sqrt_up(2.0)
1.4142135623730951

julia> sqrt_up(0.0)
0.0

julia> sqrt_up(-0.0)
-0.0
```
