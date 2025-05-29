```
sqrt_down(a)
```

Computes `sqrt(a)` with the rounding mode [`Base.Rounding.RoundDown`](https://docs.julialang.org/en/v1/base/math/#Base.Rounding.RoundDown).

```jldoctest
julia> sqrt_down(2.0)
1.414213562373095

julia> sqrt_down(0.0)
0.0

julia> sqrt_down(-0.0)
-0.0
```
