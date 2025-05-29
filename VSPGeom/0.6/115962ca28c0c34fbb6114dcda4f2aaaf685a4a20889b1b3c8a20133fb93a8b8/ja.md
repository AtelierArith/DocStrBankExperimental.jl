```
getVertices(mesh::TriMesh, icell::Int)
```

メッシュからセルの頂点を取得します

**引数**

  * `mesh::TriMesh`: [`TriMesh`](@ref) オブジェクト
  * `icell::Int`: クエリされたセルのインデックス

**戻り値**

  * `vtxs`: クエリされたセルの3つの頂点を含むベクター
