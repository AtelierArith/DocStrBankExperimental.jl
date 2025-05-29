```
setMeshEdge(meshName::String, firstVertexID::Integer, secondVertexID::Integer)
```

頂点IDからメッシュエッジを設定し、エッジIDを返します。preCICEがメッシュの接続性を必要としない場合は無視されます。

# 引数

  * `meshName::String`: エッジを追加するメッシュの名前。
  * `firstVertexID::Integer`: エッジの最初の頂点のID。
  * `secondVertexID::Integer`: エッジの2番目の頂点のID。

# 注意事項

以前の呼び出し:

  * `firstVertexID`と`secondVertexID`を持つ頂点が`meshName`のメッシュに追加されました。
