```
getneighborhood(topology, grid::AbstractGrid, cellidx::CellIndex, include_self=false)
getneighborhood(topology, grid::AbstractGrid, faceidx::FaceIndex, include_self=false)
getneighborhood(topology, grid::AbstractGrid, vertexidx::VertexIndex, include_self=false)
getneighborhood(topology, grid::AbstractGrid, edgeidx::EdgeIndex, include_self=false)
```

指定されたトポロジーによって定義された同じタイプのすべての接続されたエンティティを返します。`include_self`がtrueの場合、指定されたエンティティも返されるリストに含まれます。
