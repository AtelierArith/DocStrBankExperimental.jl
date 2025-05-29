与えられた最大次数 `nₘₐₓ` の順序-次数ペアのイテレータ。

`nₘₐₓ=2` の例：

```jldoctest
julia> collect(OrderDegreeIterator(2))
8-element Vector{Tuple{Int64, Int64}}:
 (1, -1)
 (1, 0)
 (1, 1)
 (2, -2)
 (2, -1)
 (2, 0)
 (2, 1)
 (2, 2)
```
