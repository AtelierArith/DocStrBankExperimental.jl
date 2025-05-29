```
mul(e)
```

多重辺 `e` の重複度を返します。

## 例

```jltestdoc julia> using Graphs, Multigraphs

julia> me = MultipleEdge(1, 2, 3) 多重辺 1 => 2 の重複度 3

julia> mul(me) 3
```
