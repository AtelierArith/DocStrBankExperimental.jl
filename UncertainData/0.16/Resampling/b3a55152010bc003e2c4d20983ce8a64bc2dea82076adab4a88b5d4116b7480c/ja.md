```
resample(x::UVAL_COLLECTION_TYPES, constraint::Vector{<:SamplingConstraint}, n::Int) -> Vector{Vector{T}} where T
```

`x`（不確実な値のコレクション）を `n` 回再サンプリングし、提供されたサンプリング `constraint` を適用します。

`length(x)` 要素のベクトルの `n` 要素のベクトルを返します。これらのベクトルのそれぞれは、`x` からの独立したサンプルです。各サンプルの `i` 番目の要素は、`i` 番目の不確実な値を `i` 番目のサンプリング `constraint` で切り捨て、その切り捨てた値から単一のランダムな数を引き出すことによって生成されます。

詳細は [`UVAL_COLLECTION_TYPES`](@ref) を参照してください。

## 例

```julia
# `i` 番目の値が平均 `i` で、標準偏差が `[0, 1]` の一様分布から引かれた
# 正規分布によって与えられる不確実な値を生成します。
uvals = [UncertainValue(Normal(i, rand())) for i = 1:100]

# 最初の 50 要素を `± 0.5` 標準偏差で切り捨て、最後の 50 要素を 
# `± 1.2` 標準偏差で切り捨てます。
constraints = [i <= 50 ? TruncateStd(0.5) : TruncateStd(1.2) for i = 1:100]

# 制約を要素ごとに適用し、その制約に従ったコレクションの
# 10 回の独立した実現を引き出します。
resample(uvals, constraints, 10)
```
