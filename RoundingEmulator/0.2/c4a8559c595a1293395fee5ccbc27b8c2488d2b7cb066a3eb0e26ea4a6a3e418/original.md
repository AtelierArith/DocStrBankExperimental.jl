```
div_down(a, b)
```

Computes `a / b` with the rounding mode [`Base.Rounding.RoundDown`](https://docs.julialang.org/en/v1/base/math/#Base.Rounding.RoundDown).

```jldoctest
julia> div_down(0.1, 0.3)
0.3333333333333333

julia> div_down(2.0^-100, 2.0^1000)
0.0

julia> div_down(-0.0, 1.0)
-0.0
```
