```
setMeshQuad(meshName::String, firstEdgeID::Integer, secondEdgeID::Integer, thirdEdgeID, fourthEdgeID::Integer)
```

エッジIDからメッシュQuadを設定します。

# 引数

  * `meshName::String`: Quadを追加するメッシュの名前。
  * `firstVertexID::Integer`: Quadの最初のエッジのID。
  * `secondVertexID::Integer`: Quadの2番目のエッジのID。
  * `thirdEdgeID::Integer`: Quadの3番目のエッジのID。
  * `fourthEdgeID::Integer`: Quadの4番目のエッジのID。

# 注意事項

以前の呼び出し:

  * `first_edge_id`、`second_edge_id`、`third_edge_id`、および`fourth_edge_id`を持つエッジが、ID `mesh_id`のメッシュに追加されました。
