```
add_up(a, b)
```

`a + b` を [`Base.Rounding.RoundUp`](https://docs.julialang.org/en/v1/base/math/#Base.Rounding.RoundUp) の丸めモードで計算します。

```jldoctest
julia> add_up(0.1, 0.2)
0.30000000000000004

julia> add_up(10.0^308, 10.0^308)
Inf

julia> add_up(-10.0^308, -10.0^308)
-1.7976931348623157e308

julia> add_up(-0.1, 0.1)
0.0

julia> add_up(0.0, 0.0)
0.0

julia> add_up(0.0, -0.0)
0.0

julia> add_up(-0.0, -0.0)
-0.0
```
