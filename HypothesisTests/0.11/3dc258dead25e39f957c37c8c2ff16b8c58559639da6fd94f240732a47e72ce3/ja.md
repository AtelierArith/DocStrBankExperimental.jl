```
UnequalVarianceZTest(x::AbstractVector{T<:Real}, y::AbstractVector{T<:Real})
```

`x` と `y` が平均が等しい分布から来ているという帰無仮説に対して、分布が異なる平均を持つという対立仮説のもとで、不等分散の二標本 z 検定を実行します。

実装: [`pvalue`](@ref), [`confint`](@ref)
