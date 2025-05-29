```
OneSampleTTest(x::AbstractVector{T<:Real}, y::AbstractVector{T<:Real}, μ0::Real = 0)
```

ベクトル `x` と `y` のペアの値の差が平均 `μ0` を持つ分布から来ているという帰無仮説に対して、分布が平均 `μ0` を持たないという対立仮説のペアサンプルt検定を実行します。

実装: [`pvalue`](@ref), [`confint`](@ref)

!!! note
    このテストはペアまたは依存サンプルのt検定としても知られており、ウィキペディアの[ペア差検定](https://en.wikipedia.org/wiki/Paired_difference_test)を参照してください。

