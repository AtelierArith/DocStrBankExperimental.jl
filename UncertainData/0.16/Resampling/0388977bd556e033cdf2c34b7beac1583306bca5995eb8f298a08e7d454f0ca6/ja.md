```
resample(x::UVAL_COLLECTION_TYPES, constraint::SamplingConstraint) -> Vector{T} where T
```

`x`（不確実な値のコレクション）を一度再サンプリングし、提供されたサンプリング`constraint`を適用します。

`length(x)`要素のベクターを返します。このベクターの`i`-番目の要素は、サンプリング`constraint`によって`i`-番目の不確実な値を切り捨てた後、切り捨てた値から単一のランダム数を引き出すことによって生成されます。

[`UVAL_COLLECTION_TYPES`](@ref)も参照してください。

## 例

```julia
# `i`-番目の値が平均`i`で、標準偏差が`[0, 1]`の一様分布から引かれた
# 正規分布によって与えられる不確実な値を生成します。
uvals = [UncertainValue(Normal(i, rand())) for i = 1:100]

# 各分布を±0.5標準偏差で切り捨ててから、再サンプリングします。
resample(uvals, TruncateStd(0.5))
```
