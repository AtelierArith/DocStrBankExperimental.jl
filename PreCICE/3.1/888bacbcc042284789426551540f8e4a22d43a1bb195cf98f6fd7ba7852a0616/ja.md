```
getMeshVertexIDsAndCoordinates(meshName::String)::Tuple{AbstractArray{Integer}, AbstractArray{Float64}}
```

バウンディングボックスで定義された関心領域を反復処理し、マッピングを省略して対応する座標を読み取ります。

# 引数

  * `meshName::String`: 頂点とIDを取得するメッシュの名前。

# 戻り値

  * `vertexIDs::AbstractArray{Integer}`: 頂点のID。
  * `vertexCoordinates::AbstractArray{Float64}`: 頂点の座標と対応するデータ値。形状 [N x D] で、N = 頂点の数、D = データ次元の数。
