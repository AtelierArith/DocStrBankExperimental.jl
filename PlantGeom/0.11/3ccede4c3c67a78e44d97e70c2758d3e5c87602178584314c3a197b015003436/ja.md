```
read_ops(file; attr_type=Dict{String,Any}, mtg_type=MutableNodeMTG)
```

OPSファイルを読み込み、内容を`MultiScaleTreeGraph`として返します。

# 引数

  * `file::String`: 読み込む`.ops`ファイルのパス。
  * `attr_type::Type=Dict{Symbol,Any}`: 使用する属性の型。
  * `mtg_type::Type`: 使用するMTGの型、例えば`NodeMTG`または`MutableNodeMTG`。

# 戻り値

シーンの`MultiScaleTreeGraph`で、OPFがシーンノードの子として含まれています。シーンの次元はシーンノードの`scene_dimensions`属性で利用可能です。各OPFのルートノードには、シーンによってOPFに適用された変換を格納する`scene_transformation`属性があります。これにより、シーンの変換を更新し、シーンをディスクに書き戻すことができます。OPFのルートノードには以下の属性もあります：

  * `sceneID::Int`: シーンID。
  * `plantID::Int`: 植物ID。
  * `filePath::String`: 元の`.opf`ファイルへのパス。
  * `pos::Meshes.Point`: オブジェクトの位置。
  * `scale::Float64`: オブジェクトのスケール。
  * `inclinationAzimut::Float64`: オブジェクトの傾斜方位。
  * `inclinationAngle::Float64`: オブジェクトの傾斜角。
  * `rotation::Float64`: オブジェクトの回転。
  * `functional_group::String`: オブジェクトの機能グループ。

# 詳細

OPFのノードIDは、より大きなシーンMTG内での一意性を確保するためにインポート時に再計算されます。

# 例

```julia
using CairoMakie, PlantGeom
joinpath(pathof(PlantGeom) |> dirname |> dirname, "test", "files", "scene.ops") |> read_ops |> viz
```
