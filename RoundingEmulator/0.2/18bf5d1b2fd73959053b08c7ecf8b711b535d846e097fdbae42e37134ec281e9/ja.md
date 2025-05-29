```
sub_up(a, b)
```

`a - b`を丸めモード[`Base.Rounding.RoundUp`](https://docs.julialang.org/en/v1/base/math/#Base.Rounding.RoundUp)で計算します。

```jldoctest
julia> sub_up(-0.1, 0.2)
-0.3

julia> sub_up(-10.0^308, 10.0^308)
-1.7976931348623157e308

julia> sub_up(10.0^308, -10.0^308)
Inf

julia> sub_up(0.1, 0.1)
0.0

julia> sub_up(0.0, 0.0)
0.0

julia> sub_up(0.0, -0.0)
0.0

julia> sub_up(-0.0, 0.0)
-0.0

julia> sub_up(-0.0, -0.0)
0.0
```
