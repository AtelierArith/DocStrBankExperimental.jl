```
EqualVarianceZTest(x::AbstractVector{T<:Real}, y::AbstractVector{T<:Real})
```

`x` と `y` が平均と分散が等しい分布から来ているという帰無仮説に対して、分布が異なる平均を持つが分散は等しいという対立仮説の二標本 z 検定を実行します。

実装: [`pvalue`](@ref), [`confint`](@ref)
