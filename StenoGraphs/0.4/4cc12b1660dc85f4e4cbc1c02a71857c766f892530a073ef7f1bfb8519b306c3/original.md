Single (broadcasting) arrow left (\leftarrow, Alt Gr + z)

```jldoctest
julia> @StenoGraph a ← b
b → a

julia> eltype(ans)
DirectedEdge{SimpleNode{Symbol}, SimpleNode{Symbol}}

julia> @StenoGraph [a b] ← [c d]
c → a
d → b
```
