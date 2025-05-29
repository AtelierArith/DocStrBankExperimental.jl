```
SignTest(x::AbstractVector{T<:Real}, median::Real = 0)
SignTest(x::AbstractVector{T<:Real}, y::AbstractVector{T<:Real}, median::Real = 0)
```

`x`（または`y`が提供されている場合は`x - y`）が引かれた分布の中央値が`median`であるという帰無仮説に対して、中央値が`median`と等しくないという対立仮説の符号検定を実行します。

実装: [`pvalue`](@ref), [`confint`](@ref)
