```
add_grid_layer!(m::KeplerGLMap, table, latitude::Symbol, longitude::Symbol;
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
    height_percentile = [0,100],
    height_aggregation = "average",
    elevation_percentile = [0,100],
    elevation_scale = 5,
    enable_elevation_zoom_factor = true,
    enable_3d = false)
```

地図 `m` にグリッドレイヤーを追加し、`table` からデータを描画します。

# 必須引数

  * `m::KeplerGLMap`: レイヤーを追加する地図
  * `table`: 描画に使用するデータを含む `Tables.jl` 互換のテーブル
  * `latitude::Symbol`: ヘクスビンに集約されるポイントの緯度を含む `table` の列の名前
  * `longitude::Symbol`: ヘクスビンに集約されるポイントの経度を含む `table` の列の名前

# オプション引数

  * `id = randstring(7)`: レイヤーの文字列 ID
  * `color = colorant"#762A83"`: ヘクサゴンが持つべき `Colors.jl` 互換の色（固定の場合）
  * `color_field::Symbol = :null`: ヘクサゴンの色付けに使用する `table` の列の名前
  * `color_range`: `Colors.jl` 互換の色のベクトル。生成するには `colorant"xyz"` を使用します。
  * `color_scale = "quantize"`: 値または分位数が色に使用されるべきかに応じて、`"quantize"` または `"quantile"` のいずれか。
  * `highlight_color = colorant"#762A83"`: ハイライトカラー。
  * `radius = 10.0`: 地図上のヘクサゴンの固定半径値
  * `coverage = 0.95`: カバーされるべきヘクサゴン面積の割合
  * `resolution = 8`
  * `opacity = 1.0`: ヘクサゴンの不透明度、`0.0` と `1.0` の間
  * `height_field::Symbol = :null`: ヘクサゴンの高さを決定するために使用される `table` の列の名前
  * `height_scale = "sqrt"`: `height_field` を実際の高さに変換する方法
  * `height_percentile = [0,100]`:
  * `height_aggregation = "average"`:
  * `elevation_percentile = [0,100]`:
  * `elevation_scale = 5`: 高さのスケーリングファクター
  * `enable_elevation_zoom_factor = true`
  * `enable_3d = false`: レイヤーでの3Dを有効にする

# 例

```julia
m = KeplerGL.KeplerGLMap(token)
df = CSV.read("assets/example_data/data.csv", DataFrame)
KeplerGL.add_grid_layer!(m, df, :Latitude, :Longitude, opacity = 0.5, color_field = :Magnitude, color_scale = "quantile",
    radius = 20.0, color_range = ColorBrewer.palette("BuPu",6), color_aggregation = "average", coverage = 0.95,
    height_field = :Magnitude )
```
