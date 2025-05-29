```
add_h3_layer!(m::KeplerGLMap, table, h3::Symbol;
    color = colorant"#762A83",
    color_field::Symbol = :null,
    color_range = [colorant"#762A83",colorant"#AF8DC3",colorant"#E7D4E8",colorant"#D9F0D3",colorant"#7FBF7B",colorant"#1B7837"],
    color_scale = "quantile",
    color_aggregation = "average",
    highlight_color = colorant"#762A83",
    radius = 0.6,
    coverage = 0.95,
    resolution = 8,
    opacity = 1.0,
    height_field::Symbol = :null,
    height_scale = "sqrt",
    coverage_range = [0,1],
    height_aggregation = "average",
    elevation_percentile = [0,100],
    elevation_scale = 5,
    enable_elevation_zoom_factor = true,
    enable_3d = false)

マップ `m` に H3 レイヤーを追加し、`table` からデータを描画します。

# 必須引数

  * `m::KeplerGLMap`: レイヤーを追加するマップ
  * `table`: 描画に使用するデータを含む `Tables.jl` 互換のテーブル
  * `h3::Symbol`: `table` の H3 インデックスを含む列の名前

# オプション引数

  * `id = randstring(7)`: レイヤーの文字列 ID
  * `color = colorant"#762A83"`: 六角形が持つべき `Colors.jl` 互換の色（固定の場合）
  * `color_field::Symbol = :null`: 六角形の色付けに使用する `table` の列の名前
  * `color_range`: `Colors.jl` 互換の色のベクトル。生成するには `colorant"xyz"` を使用します。
  * `color_scale = "quantize"`: 値または分位数が色に使用されるかに応じて、`"quantize"` または `"quantile"` のいずれか。
  * `highlight_color = colorant"#762A83"`: ハイライトカラー。
  * `coverage = 0.95`: カバーすべき六角形の面積の割合
  * `opacity = 1.0`: 六角形の不透明度、`0.0` と `1.0` の間
  * `height_field::Symbol = :null`: 六角形の高さを決定するために使用する `table` の列の名前
  * `height_scale = "sqrt"`: `height_field` を実際の高さに変換する方法
  * `height_range = [0,500]`: 列の高さの範囲
  * `coverage_field = :null`: 六角形のカバレッジを決定するために使用する `table` の列の名前
  * `coverage_scale = "linear"`: `coverage_field` を実際のカバレッジに変換する方法
  * `coverage_range = [0,1]`: カバレッジの範囲
  * `elevation_scale = 5`: 高さのスケーリングファクター
  * `enable_elevation_zoom_factor = true`
  * `enable_3d = false`: レイヤーで 3D を有効にする

# 例

```

julia using H3, H3.API m = KeplerGL.KeplerGLMap(token) df = CSV.read("assets/example*data/data.csv", DataFrame) coord = H3.Lib.GeoCoord.(deg2rad.(df.Latitude), deg2rad.(df.Longitude) ) h3 = H3.API.geoToH3.(coord, 5) df.h3str = H3.API.h3ToString.(h3) KeplerGL.add*h3*layer!(m, df, :h3str,     color = colorant"rgb(23,184,190)", color*field = :Magnitude, color*scale = "quantize",     color*range = ColorBrewer.palette("PRGn", 6)); ```
