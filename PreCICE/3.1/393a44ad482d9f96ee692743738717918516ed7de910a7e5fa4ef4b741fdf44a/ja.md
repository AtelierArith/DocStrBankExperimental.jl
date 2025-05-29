```
setMeshTetrahedron(meshName::String, firstEdgeID::Integer, secondEdgeID::Integer, thirdEdgeID::Integer, fourthEdgeID::Integer)
```

エッジIDからメッシュテトラヘドロンを設定します。

# 引数

  * `meshName::String`: テトラヘドロンを追加するメッシュの名前。
  * `firstEdgeID::Integer`: テトラヘドロンの最初のエッジのID。
  * `secondEdgeID::Integer`: テトラヘドロンの2番目のエッジのID。
  * `thirdEdgeID::Integer`: テトラヘドロンの3番目のエッジのID。
  * `fourthEdgeID::Integer`: テトラヘドロンの4番目のエッジのID。

# 注意事項

以前の呼び出し:

  * `first_edge_id`、`second_edge_id`、`third_edge_id`、および `fourth_edge_id` を持つエッジが、ID `mesh_id` のメッシュに追加されました。
