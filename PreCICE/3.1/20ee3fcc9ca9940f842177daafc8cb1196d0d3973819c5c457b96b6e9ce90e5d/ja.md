```
    readData(meshName::String, dataName::String, valueIndices::AbstractArray{Cint}, relativeReadTime::Float64)
```

メッシュのデータから指定された頂点の値を読み取ります。値は頂点によって指定された順序で行列に読み込まれます。

値の1D/スカラー形式は長さNのベクトルです。値の2D形式は[N x 2]です。値の3D形式は[N x 3]です。ここでNは頂点の数です。

データはrelativeReadTimeで読み取られ、これは現在の時間ステップの開始から測定された時点を示します。`relativeReadTime = 0`は時間ステップの開始時のデータに対応します。ユーザーが時間ステップの終わりに`advance(dt)`を呼び出すと仮定すると、`dt`は現在の時間ステップのサイズを示します。したがって、`relativeReadTime = dt`は時間ステップの終わりのデータに対応します。

# 引数

  * `meshName::String`: データを読み取るメッシュの名前。
  * `dataName::String`: 読み取るデータの名前。
  * `valueIndices::AbstractArray{Cint}`: データを読み取る頂点の頂点ID。
  * `relativeReadTime::Float64`: 現在の時間ステップの開始からの相対的な時点でデータを読み取るためのもの。

# 戻り値

  * `values::AbstractArray{Float64}`: preCICEから読み取った値。形状は[N x D]で、Nは頂点の数、Dはデータの次元数です。

# 注意事項

  * 頂点のすべてのVertexIDはsetMeshVertexまたはsetMeshVerticesの戻り値です。
  * `size(values) == (length(valueIndices), getDataDimensions(meshName, dataName))`
