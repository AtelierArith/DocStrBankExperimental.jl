```
winsor(x::AbstractVector; prop=0.0, count=0)
```

`x`のすべての要素のイテレータを返し、最高の要素のうち`count`または比例`prop`を前の最高の要素で置き換え、同じ数の最低の要素を次の最低の要素で置き換えます。

置き換えられる要素の数は、いくつかの要素が下限または上限と等しい場合、指定された数よりも少なくなる可能性があります。

`x`のウィンザー平均を計算するには、`mean(winsor(x))`を使用します。

# 例

```jldoctest
julia> collect(winsor([5,2,3,4,1], prop=0.2))
5-element Vector{Int64}:
 4
 2
 3
 4
 2
```
