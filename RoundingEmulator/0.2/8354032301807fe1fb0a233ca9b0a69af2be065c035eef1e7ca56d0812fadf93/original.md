```
mul_down(a, b)
```

Computes `a * b` with the rounding mode [`Base.Rounding.RoundDown`](https://docs.julialang.org/en/v1/base/math/#Base.Rounding.RoundDown).

```jldoctest
julia> mul_down(0.1, 0.2)
0.02

julia> mul_down(10.0^308, 10.0^308)
1.7976931348623157e308

julia> mul_down(10.0^308, -10.0^308)
-Inf

julia> mul_down(5.0e-324, 5.0e-324)
0.0

julia> mul_down(-0.1, 0.1)
-0.010000000000000002

julia> mul_down(0.0, 0.0)
0.0

julia> mul_down(0.0, -0.0)
-0.0

julia> mul_down(-0.0, -0.0)
0.0
```
