```markdown
addboundaryfacetset!(grid::AbstractGrid, topology::ExclusiveTopology, name::String, f::Function; all::Bool=true)

グリッドにキー `name` を持つ境界ファセットセットを追加します。ファセットセットは、`String` キーを `(global_cell_id, local_facet_id)` に対応するタプルの `OrderedSet` にマッピングします。ファセットセットは、`ConstraintHandler` の境界を指定するために必要な `Dirichlet` 構造体を初期化するために使用されます。`all=true` は、ファセットがセットに追加されるべき場合、ファセット上のすべてのノード座標 `x` に対して `f(x)` が `true` を返す必要があることを意味します。そうでない場合、`f(x)` が1つのノードに対して `true` を返すだけで十分です。
```
