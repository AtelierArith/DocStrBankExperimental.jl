単一（ブロードキャスティング）矢印右（\rightarrow, Alt Gr + i）

```jldoctest
julia> @StenoGraph a → b
a → b

julia> eltype(ans)
DirectedEdge{SimpleNode{Symbol}, SimpleNode{Symbol}}

julia> @StenoGraph [a b] → [c d]
a → c
b → d
```
