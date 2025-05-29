```
read_ops_file(file)
```

`.ops`ファイルの内容を読み取り、シーンの寸法とオブジェクトテーブルを含むタプルを返します。

# 引数

  * `file::String`: 読み取る`.ops`ファイルのパス。

# 戻り値

シーンの寸法とオブジェクトテーブルを含むタプル。シーンの寸法は、原点とシーンの反対点を持つ2つの`Meshes.Point`のタプルです。オブジェクトテーブルは、以下のフィールドを持つ`NamedTuple`の配列です：

  * `sceneID::Int`: シーンID。
  * `plantID::Int`: プラントID。
  * `filePath::String`: `.opf`ファイルへのパス。
  * `pos::Meshes.Point`: オブジェクトの位置。
  * `scale::Float64`: オブジェクトのスケール。
  * `inclinationAzimut::Float64`: オブジェクトの傾斜方位。
  * `inclinationAngle::Float64`: オブジェクトの傾斜角。
  * `rotation::Float64`: オブジェクトの回転。
  * `functional_group::String`: オブジェクトの機能グループ。
