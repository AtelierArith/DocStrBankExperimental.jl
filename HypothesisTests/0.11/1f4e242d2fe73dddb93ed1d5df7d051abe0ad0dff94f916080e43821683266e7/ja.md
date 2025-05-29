```
ExactSignedRankTest(x::AbstractVector{<:Real}[, y::AbstractVector{<:Real}])
```

`x`（または`y`が提供されている場合は`x - y`の差）の分布がゼロの中央値を持つという帰無仮説に対して、中央値がゼロでないという対立仮説のウィルコクソンの正確な符号順位U検定を実行します。

順位が tied でない場合、正確な p 値は `StatsFuns` パッケージの `signrankcdf` および `signrankccdf` 関数を使用して計算されます。順位が tied の場合、p 値は全ての置換の列挙によって計算され、これは中程度のサイズのデータセットでも非常に遅くなる可能性があります。

実装: [`pvalue`](@ref), [`confint`](@ref)
