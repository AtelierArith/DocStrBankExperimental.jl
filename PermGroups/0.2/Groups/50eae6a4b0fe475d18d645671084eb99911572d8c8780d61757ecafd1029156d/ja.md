`Group(l::AbstractVector{T}[,one]) where T`

グループは、同じ型の `l` 要素のリストから構築されることがあります。これらの要素は、関数 `*` と `inv` に応答する必要があります。もし `l` から `one` を計算することができない場合（例えば、`l[1]` が `one` に応答しない、または `l` が空で `T` が `one` に応答しない場合）、グループの単位元を第二引数として与える必要があります。

```julia-repl
julia> G=Group([[-1 -1;1 0]])
Group([[-1 -1; 1 0]])

julia> elements(G)
3-element Vector{Matrix{Int64}}:
 [1 0; 0 1]
 [-1 -1; 1 0]
 [0 1; -1 -1]
```
