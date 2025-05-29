```
read_inp(file::String)
```

Abaqus .inpファイルを読み込み、[`AbaqusReader.jl`](https://github.com/JuliaFEM/AbaqusReader.jl)パッケージの助けを借りてメッシュをポイントクラウドに変換します。すべての要素はポイントに変換されます。要素の中心がポイントの位置になり、要素の体積がポイントの体積になります。Abaqusで定義された要素セットは、対応するポイントセットに変換されます。

現在サポートされているメッシュ要素: [:Tet4, :Hex8]

# 引数

  * `file::String`: Abaqus .inpファイルへのパス。

# 戻り値

  * `position::Matrix{Float64}`: ポイントの位置（各要素の中点）。
  * `volume::Vector{Float64}`: ポイントの体積（各要素の体積）。
  * `point_sets`: .inpファイルで定義された要素セット。
