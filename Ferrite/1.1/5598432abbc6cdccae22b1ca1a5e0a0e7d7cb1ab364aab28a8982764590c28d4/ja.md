```
getnodes(grid::AbstractGrid)
getnodes(grid::AbstractGrid, v::Union{Int,Vector{Int}}
getnodes(grid::AbstractGrid, setname::String)
```

`<:AbstractGrid`のすべての`nodes::Collection{N}`を返すか、`Int`、`Vector{Int}`、または`String`に基づいてサブセットを返します。最後のオプションは、`<:AbstractGrid`の`nodeset`を呼び出そうとします。`Collection{N}`は、各要素がノードに対応するインデックス可能なコレクションを指します。
