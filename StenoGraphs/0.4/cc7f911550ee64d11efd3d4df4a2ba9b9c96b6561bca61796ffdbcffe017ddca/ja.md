左右の単一（ブロードキャスト）矢印 (\leftrightarrow)

```jldoctest
julia> @StenoGraph a ↔ b
a ↔ b

julia> eltype(ans)
UndirectedEdge{SimpleNode{Symbol}, SimpleNode{Symbol}}

julia> @StenoGraph [a b] ↔ [c d]
a ↔ c
b ↔ d
```
