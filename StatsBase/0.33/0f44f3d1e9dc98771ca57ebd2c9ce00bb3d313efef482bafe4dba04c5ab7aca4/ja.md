```
trim(x::AbstractVector; prop=0.0, count=0)
```

`x`のすべての要素のイテレータを返し、最高および最低の要素のうち、`count`または比例`prop`のいずれかを省略します。

トリミングされた要素の数は、いくつかの要素が下限または上限に等しい場合、指定された数よりも少なくなる可能性があります。

`x`のトリミングされた平均を計算するには`mean(trim(x))`を使用します。分散を計算するには`trimvar(x)`を使用します（[`trimvar`](@ref)を参照）。

# 例

```julia
julia> collect(trim([5,2,4,3,1], prop=0.2))
3-element Array{Int64,1}:
 2
 4
 3
```
