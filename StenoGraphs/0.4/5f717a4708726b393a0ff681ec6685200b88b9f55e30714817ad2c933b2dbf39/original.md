Double (cross product) arrow left-right (\Leftrightarrow)

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
