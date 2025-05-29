```
gdalwrite(fname::AbstractString, data, opts=String[]; kwargs...)
```

ラスタまたはベクターファイルをディスクに書き込む

  * `fname`: 出力ファイル名。`opts`で明示的に選択されていない場合、使用されるドライバーはファイル拡張子から選ばれます。
  * `data`: ファイルに保存されるデータ。GMTタイプまたはGDALデータセットであることができます。
  * `opts`: オプションのリスト。受け入れられるオプションはgdal_translateまたはogr2ogrユーティリティのものです。このリストは文字列のベクターの形、または単一の文字列に結合された形で提供できます。
  * `kwargs`: このオプションはGMT領域（-R）およびインクリメント（-I）を受け入れます。

または

```
gdalwrite(cube::GItype, fname::AbstractString, v=nothing; dim_name::String="time", dim_units::String="")
```

MxNxP `cube`オブジェクトをマルチレイヤーファイルとしてディスクに書き込む。

  * `cube`: GMTgridまたはGMTimageキューブ
  * `fname`: `cube`を保存するファイル名
  * `v`: Z層の座標を持つベクター（省略した場合は1:size(cube,3)として作成）
  * `dim_name`: $垂直$次元の変数の名前。
  * `dim_units`: `v`ベクターの単位。提供されていない場合は、存在する場合は`cube.z_units`を使用します（GMTgridのみ）。
