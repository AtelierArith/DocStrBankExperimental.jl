```
p_value(vc::VariationCall) -> Union{Nothing,Float64}
```

`vc`の観測統計量の$p$-値を取得します。未知の場合は`nothing`を返します。

関連情報は[`variation_test`](@ref)を参照してください。
