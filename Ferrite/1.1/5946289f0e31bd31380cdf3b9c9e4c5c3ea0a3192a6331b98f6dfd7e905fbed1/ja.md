addboundaryvertexset!(grid::AbstractGrid, topology::ExclusiveTopology, name::String, f::Function; all::Bool=true)

境界頂点集合をキー `name` でグリッドに追加します。頂点集合は、`String` キーを `(global_cell_id, local_vertex_id)` に対応するタプルの `OrderedSet` にマッピングします。`all=true` は、ファセットが集合に追加されるべき場合、ファセット上のすべてのノード座標 `x` に対して `f(x)` が `true` を返す必要があることを意味します。そうでない場合は、1つのノードに対して `f(x)` が `true` を返すだけで十分です。
