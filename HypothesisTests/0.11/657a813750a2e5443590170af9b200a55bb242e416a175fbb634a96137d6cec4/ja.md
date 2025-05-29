```
OneSampleZTest(x::AbstractVector{T<:Real}, y::AbstractVector{T<:Real}, μ0::Real = 0)
```

ベクトル `x` と `y` のペアの値の差が平均 `μ0` を持つ分布から来ているという帰無仮説に対するペアサンプルz検定を行います。対立仮説は、その分布が平均 `μ0` を持たないというものです。

実装: [`pvalue`](@ref), [`confint`](@ref)
