```
resample(x::UVAL_COLLECTION_TYPES, constraint::Vector{<:SamplingConstraint}) -> Vector{T} where T
```

`x`（不確実な値のコレクション）を一度再サンプリングし、提供されたサンプリング`constraint`を適用します。制約の数は`x`の要素数と一致する必要があります。

`length(x)`要素のベクトルを返します。このベクトルの`i`-番目の要素は、`i`-番目の不確実な値を`i`-番目のサンプリング`constraint`で切り捨て、その切り捨てた値から単一のランダム数を引き出すことによって生成されます。

詳細は[`UVAL_COLLECTION_TYPES`](@ref)を参照してください。

## 例

```julia
# `i`-番目の値が平均`i`、標準偏差が`[0, 1]`の一様分布から引かれた
# 正規分布によって与えられる不確実な値を生成します。
uvals = [UncertainValue(Normal(i, rand())) for i = 1:100]

# 各分布を±0.5標準偏差で切り捨て、再サンプリングします。
resample(uvals, TruncateStd(0.5))
```
