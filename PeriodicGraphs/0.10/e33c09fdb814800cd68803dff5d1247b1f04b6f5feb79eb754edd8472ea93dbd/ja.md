```
PeriodicGraph([nv::Integer, ]edge_list::AbstractVector{PeriodicEdge{N}})
PeriodicGraph{N}([nv::Integer, ]edge_list::AbstractVector{PeriodicEdge{N}})
```

`PeriodicGraph{N}`をエッジのベクトルから構築します。`nv`が指定されていない場合、頂点の数は`edge_list`のエッジで使用されている最大の値になります。

### 実装ノート

このコンストラクタは、`edge_list`が辞書順でソートされており、重複が含まれていない場合に最も速く動作します。

## 例

```jldoctest
julia> el = PeriodicEdge2D[(1, 1, (1,0)), (1, 3, (0,1)), (3, 1, (0,-1))];

julia> g = PeriodicGraph(el)
PeriodicGraph2D(3, PeriodicEdge2D[(1, 1, (1,0)), (1, 3, (0,1))])

julia> ne(g)
2
```
