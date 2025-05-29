ダブル（外積）矢印 左右 (\Leftrightarrow)

```jldoctest
julia> @StenoGraph a ⇔ b
a ↔ b

julia> eltype(ans)
UndirectedEdge{SimpleNode{Symbol}, SimpleNode{Symbol}}

julia> @StenoGraph [a b] ⇔ [c d]
a ↔ c
a ↔ d
b ↔ c
b ↔ d
```
