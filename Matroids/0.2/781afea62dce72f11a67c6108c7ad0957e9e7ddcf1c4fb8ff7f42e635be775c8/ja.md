```
TransversalMatroid(m::Int, the_sets::Vector{Set{T}}) where {T<:Integer}
```

基底集合 `S={1,2,...,m}` を持つ横断マトロイドを作成します。リスト `the_sets` のすべての集合は `S` の部分集合である必要があります。
