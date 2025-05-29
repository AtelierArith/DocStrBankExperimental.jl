```
addfacetset!(grid::AbstractGrid, name::String, faceid::AbstractVecOrSet{FacetIndex})
addfacetset!(grid::AbstractGrid, name::String, f::Function; all::Bool=true)
```

グリッドにキー `name` を持つファセットセットを追加します。ファセットセットは、`String` キーを `(global_cell_id, local_facet_id)` に対応するタプルの `OrderedSet` にマッピングします。ファセットセットは、`ConstraintHandler` の `Dirichlet` 境界条件を初期化するために使用できます。`all=true` は、ファセットがセットに追加されるべき場合、`f(x)` がファセット上のすべてのノード座標 `x` に対して `true` を返す必要があることを意味します。そうでない場合、`f(x)` が1つのノードに対して `true` を返すだけで十分です。

```julia
addfacetset!(grid, "right", Set((FacetIndex(2,2), FacetIndex(4,2)))) #参照のためにグリッドマニュアルの例を見てください
addfacetset!(grid, "clamped", x -> norm(x[1]) ≈ 0.0) #参照のために非圧縮弾性の例を見てください
```
