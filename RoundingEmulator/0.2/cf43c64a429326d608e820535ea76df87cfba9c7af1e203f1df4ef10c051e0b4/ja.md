```
sqrt_down(a)
```

`sqrt(a)`を丸めモード[`Base.Rounding.RoundDown`](https://docs.julialang.org/en/v1/base/math/#Base.Rounding.RoundDown)で計算します。

```jldoctest
julia> sqrt_down(2.0)
1.414213562373095

julia> sqrt_down(0.0)
0.0

julia> sqrt_down(-0.0)
-0.0
```
