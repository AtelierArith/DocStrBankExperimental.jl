```
resample(x::UVAL_COLLECTION_TYPES, constraint::SamplingConstraint, n::Int) -> Vector{Vector{T}} where T
```

`x`（不確実な値のコレクション）を `n` 回再サンプリングし、提供されたサンプリング `constraint` を適用します。

`length(x)` 要素のベクトルの `n` 要素のベクトルを返します。これらのベクトルのそれぞれは、`x` からの独立したサンプルです。各サンプルの `i` 番目の要素は、サンプリング `constraint` によって `i` 番目の不確実な値を切り捨て、その切り捨てた値から単一のランダム数を引き出すことによって生成されます。

[`UVAL_COLLECTION_TYPES`](@ref) も参照してください。

## 例

```julia
# `i` 番目の値が平均 `i` で、標準偏差が `[0, 1]` の一様分布から引き出された
# 正規分布によって与えられる不確実な値を生成します。
uvals = [UncertainValue(Normal(i, rand())) for i = 1:100]

# 最初の 50 要素を 90 パーセンタイル範囲で切り捨て、最後の 50 要素を 40 パーセンタイル範囲で切り捨てます。
constraints = [i <= 50 ? TruncateQuantiles(0.05, 0.95) : TruncateQuantiles(0.3, 0.7) for i = 1:100]

# 分布を切り捨て、次に提供された制約に従ってコレクションの 10 回の独立した実現を引き出します。
resample(uvals, constraints, 10)
```
