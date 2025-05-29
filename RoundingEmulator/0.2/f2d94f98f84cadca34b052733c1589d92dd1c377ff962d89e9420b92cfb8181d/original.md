```
sub_down(a, b)
```

Computes `a - b` with the rounding mode [`Base.Rounding.RoundDown`](https://docs.julialang.org/en/v1/base/math/#Base.Rounding.RoundDown).

```jldoctest
julia> sub_down(-0.1, 0.2)
-0.30000000000000004

julia> sub_down(-10.0^308, 10.0^308)
-Inf

julia> sub_down(10.0^308, -10.0^308)
1.7976931348623157e308

julia> sub_down(0.1, 0.1)
-0.0

julia> sub_down(0.0, 0.0)
-0.0

julia> sub_down(0.0, -0.0)
0.0

julia> sub_down(-0.0, 0.0)
-0.0

julia> sub_down(-0.0, -0.0)
-0.0
```
