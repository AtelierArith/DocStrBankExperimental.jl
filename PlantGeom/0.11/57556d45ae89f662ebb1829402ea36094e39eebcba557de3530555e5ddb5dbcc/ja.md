```
write_ops(file, scene_dimensions, object_table)
```

シーンファイル（`.ops`）を、指定された寸法とオブジェクトテーブルで書き込みます。

# 引数

  * `file::String`: 書き込む`.ops`ファイルのパス。
  * `scene_dimensions::Tuple{Meshes.Point{3,T},Meshes.Point{3,T}}`: シーンの寸法。
  * `object_table`: `.ops`ファイルに書き込むオブジェクトのテーブル。このテーブルには以下の列が含まれる場合があります。

      * `sceneID::Int`: シーンID（必須）。
      * `plantID::Int`: プラントID（必須）。
      * `filePath::String`: `.opf`ファイルへのパス（必須）。
      * `pos::Meshes.Point{3,T}`: オブジェクトの位置（必須）。
      * `functional_group::String`: オブジェクトの機能グループ、オブジェクトをモデルにマッピングするために使用されます（必須）。
      * `scale::T`: オブジェクトのスケール（オプション、デフォルトは0.0）。
      * `inclinationAzimut::T`: オブジェクトの傾斜方位（オプション、デフォルトは0.0）。
      * `inclinationAngle::T`: オブジェクトの傾斜角（オプション、デフォルトは0.0）。
      * `rotation::T`: オブジェクトの回転（オプション、デフォルトは0.0）。

# 詳細

`object_table`は、`Tables.jl`インターフェースを実装する任意の形式であることができます。*例*として、`NamedTuple`の配列や`DataFrame`などがあります...

# 例

```julia
using Meshes
using Tables
using PlantGeom

scene_dimensions = (Meshes.Point(0.0, 0.0, 0.0), Meshes.Point(100.0, 100.0, 100.0))
positions = [Meshes.Point(50.0, 50.0, 50.0), Meshes.Point(60.0, 60.0, 60.0), Meshes.Point(70.0, 70.0, 70.0)]
object_table = [
    (sceneID=1, plantID=p, filePath="opf/plant_$p.opf", pos=positions[p], functional_group="plant", rotation=0.1) for p in 1:3
]

write_ops("scene.ops", scene_dimensions, object_table)
```
