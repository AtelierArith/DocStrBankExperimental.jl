```
wrapdims(::NamedTuple)
wrapdims(::NamedTuple, ::Symbol)
```

`NamedTuple`のキーを1次元の`KeyedArray`のキーに変換します。次元名が提供されると、`NamedDimsArray`ラッパーも追加されます。

# 例

```jldoctest
julia> wrapdims((alpha=1, beta=20))
1-dimensional KeyedArray(...) with keys:
↓   2-element Vector{Symbol}
And data, 2-element Vector{Int64}:
 (:alpha)   1
 (:beta)   20

julia> push!(ans, :gamma => 300)
1-dimensional KeyedArray(...) with keys:
↓   3-element Vector{Symbol}
And data, 3-element Vector{Int64}:
 (:alpha)    1
 (:beta)    20
 (:gamma)  300
```
