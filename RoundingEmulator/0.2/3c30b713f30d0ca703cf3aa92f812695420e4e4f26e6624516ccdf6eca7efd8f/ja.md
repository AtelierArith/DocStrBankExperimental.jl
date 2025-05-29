```
div_up(a, b)
```

`a / b` を丸めモード [`Base.Rounding.RoundUp`](https://docs.julialang.org/en/v1/base/math/#Base.Rounding.RoundUp) で計算します。

```jldoctest
julia> div_up(0.1, 0.3)
0.33333333333333337

julia> div_up(2.0^-100, 2.0^1000)
5.0e-324

julia> div_up(-0.0, 1.0)
-0.0
```
