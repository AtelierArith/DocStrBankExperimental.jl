```
    writeData(meshName::String, dataName::String, valueIndices::AbstractArray{Cint}, values::AbstractArray{Float64})
```

指定された頂点の値をメッシュのデータに書き込みます。値は行列として提供されます。提供されたデータの順序は、頂点によって指定された順序に従います。

値の1D/スカラー形式は長さNのベクトルです。値の2D形式は[N x 2]です。値の3D形式は[N x 3]です。ここで、Nは頂点の数です。

# 引数

  * `meshName::String`: データを書き込むメッシュの名前。
  * `dataName::String`: 書き込むデータの名前。
  * `valueIndices::AbstractArray{Cint}`: データを書き込む頂点の頂点ID。形状は[N x 1]で、Nは頂点の数です。
  * `values::AbstractArray{Float64}`: preCICEに書き込む値。形状は[N x D]で、Nは頂点の数、Dはデータの次元数です。

# 注意事項

以前の呼び出し:

  * `valueIndices`のすべてのVertexIDはsetMeshVertexまたはsetMeshVerticesの戻り値です。
  * `size(values) == (length(valueIndices), getDataDimensions(meshName, dataName))`

参照:

  * [`setMeshVertex`](@ref)
  * [`setMeshVertices`](@ref)
  * [`getDataDimensions`](@ref)

```
