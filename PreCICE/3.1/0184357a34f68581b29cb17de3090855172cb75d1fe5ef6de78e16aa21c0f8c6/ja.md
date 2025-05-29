```
setMeshQuads(meshName::String, vertices::AbstractArray{Integer})
```

頂点IDからメッシュクワッドを設定します。

# 引数

  * `meshName::String`: クワッドを追加するメッシュの名前。
  * `vertices::AbstractArray{Integer}`: クワッドのエッジのID。形状は [N x 4] で、N はクワッドの数です。
