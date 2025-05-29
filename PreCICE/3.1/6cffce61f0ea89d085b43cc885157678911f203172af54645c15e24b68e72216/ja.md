```
writeGradientData(meshName::String, dataName::String, valueIndices::AbstractArray{Cint}, gradientValues::AbstractArray{Float64})
```

指定された頂点の勾配値をメッシュのデータに書き込みます。

2つの頂点を持つ2D問題の形式は[v1x*dx v1y*dx v1x*dy v1y*dy; v2x*dx v2y*dx v2x*dy v2y*dy]です。2つの頂点を持つ3D問題の形式は[v1x*dx v1y*dx v1z*dx v1x*dy v1y*dy v1z*dy v1x*dz v1y*dz v1z*dz; v2x*dx v2y*dx v2z*dx v2x*dy v2y*dy v2z*dy v2x*dz v2y*dz v2z*dz]です。

# 引数

  * `meshName::String`: データを書き込むメッシュの名前。
  * `dataName::String`: 書き込むデータの名前。
  * `valueIndices::AbstractArray{Cint}`: 頂点のインデックス。
  * `gradientValues::AbstractArray{Float64}`: 書き込む勾配値。

# 注意事項

以前の呼び出し:

  * [`initialize`](@ref)

# 例

2つの頂点を持つ2D問題のベクトルデータの勾配値を書き込みます:

```julia
valueIndices = [1, 2]
gradientValues = [1.0 2.0 3.0 4.0; 5.0 6.0 7.0 8.0]
PreCICE.writeGradientData("MeshOne", "DataOne", valueIndices, gradientValue)
```
