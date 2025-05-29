```
setMeshTetrahedra(meshName::String, vertices::AbstractArray{Integer})
```

頂点IDからメッシュテトラヘドラを設定します。

# 引数

  * `meshName::String`: テトラヘドラを追加するメッシュの名前。
  * `vertices::AbstractArray{Integer}`: テトラヘドラのエッジのID。形状は[N x 4]で、Nはテトラヘドラの数です。
