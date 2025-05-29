```
mul_up(a, b)
```

`a * b` を丸めモード [`Base.Rounding.RoundUp`](https://docs.julialang.org/en/v1/base/math/#Base.Rounding.RoundUp) で計算します。

```jldoctest
julia> mul_up(0.1, 0.2)
0.020000000000000004

julia> mul_up(10.0^308, 10.0^308)
Inf

julia> mul_up(10.0^308, -10.0^308)
-1.7976931348623157e308

julia> mul_up(5.0e-324, 5.0e-324)
5.0e-324

julia> mul_up(-0.1, 0.1)
-0.01

julia> mul_up(0.0, 0.0)
0.0

julia> mul_up(0.0, -0.0)
-0.0

julia> mul_up(-0.0, -0.0)
0.0
```
