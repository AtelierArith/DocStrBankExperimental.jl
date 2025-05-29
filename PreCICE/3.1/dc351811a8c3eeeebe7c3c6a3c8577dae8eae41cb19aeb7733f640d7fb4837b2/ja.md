```
setMeshTriangle(meshName::String, firstEdgeID::Integer, secondEdgeID::Integer, thirdEdgeID::Integer)
```

頂点IDからメッシュ三角形を設定します。

# 引数

  * `meshName::String`: エッジを追加するメッシュの名前。
  * `firstVertexID::Integer`: エッジの最初の頂点のID。
  * `secondVertexID::Integer`: エッジの2番目の頂点のID。
  * `thirdVertexID::Integer`: 三角形の3番目のエッジのID。

# 注意事項

以前の呼び出し:

  * `first_edge_id`、`second_edge_id`、および `third_edge_id` を持つエッジが、名前 `meshName` のメッシュに追加されました。
