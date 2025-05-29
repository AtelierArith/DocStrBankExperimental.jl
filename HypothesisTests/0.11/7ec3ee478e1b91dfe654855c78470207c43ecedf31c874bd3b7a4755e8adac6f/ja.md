```
SignedRankTest(x::AbstractVector{<:Real})
SignedRankTest(x::AbstractVector{<:Real}, y::AbstractVector{<:Real})
```

`x`（または`y`が提供されている場合は`x - y`の差）の分布がゼロの中央値を持つという帰無仮説に対して、中央値がゼロでないという対立仮説のウィルコクソン符号付き順位検定を実行します。

順位が tied でなく、サンプル数が ≤50 の場合、または順位が tied でありサンプル数が ≤15 の場合、`SignedRankTest` は正確な符号付き順位検定を実行します。それ以外の場合、`SignedRankTest` は近似符号付き順位検定を実行します。動作は、[`ExactSignedRankTest`](@ref) または [`ApproximateSignedRankTest`](@ref) を直接使用することでさらに制御できます。

実装: [`pvalue`](@ref), [`confint`](@ref) ```
