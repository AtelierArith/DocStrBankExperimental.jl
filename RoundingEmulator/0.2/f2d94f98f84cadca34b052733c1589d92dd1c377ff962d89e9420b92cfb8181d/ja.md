```
sub_down(a, b)
```

`a - b` を丸めモード [`Base.Rounding.RoundDown`](https://docs.julialang.org/en/v1/base/math/#Base.Rounding.RoundDown) で計算します。

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
