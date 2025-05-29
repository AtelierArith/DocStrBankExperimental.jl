```
renumberconn!(fes::AbstractFESet, new_numbering::AbstractVector{IT}) where {IT<:Integer}
```

有限要素の接続性に基づいてノードの番号を新しい番号付けに基づいて再番号付けします。

`fes` = 有限要素セット `new_numbering` = ノードの新しい連番。接続性は `conn[j]` –> `new_numbering[conn[j]]` のように変更されるべきです。

接続されていないノードがあり、それをメッシュから削除したいとしましょう。以下のようにしてそれを実現できます。

```
connected = findunconnnodes(fens, fes);
fens, new_numbering = compactnodes(fens, connected);
fes = renumberconn!(fes, new_numbering);
```

最後に、メッシュが有効であることを確認します：

```julia
validate_mesh(fens, fes);
```
