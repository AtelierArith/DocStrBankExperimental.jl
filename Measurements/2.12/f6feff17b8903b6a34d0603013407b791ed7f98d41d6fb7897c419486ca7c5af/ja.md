```
measurement(string) -> Measurement{Float64}
```

文字列を解析し、`Measurement{Float64}`オブジェクトを返します。

有効な文字列の例と、それに対応する`Measurement{Float64}`は次のとおりです。

```jldoctest
julia> using Measurements

julia> measurement("-123.4(56)")
-123.4 ± 5.6

julia> measurement("+1234(56)e-1")
123.4 ± 5.6

julia> measurement("12.34e-1 +- 0.56e1")
1.2 ± 5.6

julia> measurement("(-1.234 ± 0.056)e2")
-123.4 ± 5.6

julia> measurement("1234e-1 +/- 5.6e0")
123.4 ± 5.6

julia> measurement("-1234e-1")
-123.4 ± 0.0
```
