```
add_polygon_layer!(m::KeplerGLMap, table, geojson::Symbol;
    color = colorant"#762A83",
    color_field::Symbol = :null,
    color_range = [colorant"#762A83",colorant"#AF8DC3",colorant"#E7D4E8",colorant"#D9F0D3",colorant"#7FBF7B",colorant"#1B7837"],
    color_scale = "quantize",
    highlight_color = colorant"#762A83",
    filled = true,
    opacity = 1.0,
    outline = false,
    outline_opacity = 1.0,
    outline_thickness = 2.0,
    outline_color = colorant"#000000",
    outline_color_field::Symbol = :null,
    outline_color_range = [colorant"#FFFFFF", colorant"#000000"],
    outline_color_scale = "quantile",
    outline_width_field::Symbol = :null,
    outline_width_scale = "linear",
    height_field::Symbol = :null,
    height_scale = "linear",
    elevation_scale = 1.0,
    enable_elevation_zoom_factor = true,
    enable_3d = false)
```

地図 `m` にポリゴンレイヤーを追加し、`table` からデータを描画します。

# 必須引数

  * `m::KeplerGLMap`: レイヤーを追加する地図
  * `table`: 描画に使用するデータを含む `Tables.jl` 互換のテーブル
  * `geojson::Symbol`: GeoJSON形式のフィーチャを含む `table` の列の名前

# オプション引数

  * `id = randstring(7)`: レイヤーの文字列ID
  * `color = colorant"#762A83"`: 形状が持つべき `Colors.jl` 互換の色（固定の場合）
  * `color_field::Symbol = :null`: 形状の色付けに使用する `table` の列の名前
  * `color_range`: `Colors.jl` 互換の色のベクトル。生成するには `colorant"xyz"` を使用します。
  * `color_scale = "quantize"`: 値または分位数が色に使用されるべきかに応じて、`"quantize"` または `"quantile"` のいずれか。
  * `highlight_color = colorant"#762A83"`: ハイライトカラー。
  * `filled = true`: ポリゴンが塗りつぶされているかどうか。
  * `opacity = 1.0`: 点の不透明度、`0.0` と `1.0` の間
  * `outline = false`: 点マーカーにアウトラインがあるべきかどうか
  * `outline_thickness = 2.0`: アウトラインの厚さ
  * `outline_color = colorant"#000000"`: 点のアウトラインが持つべき `Colors.jl` 互換の色（固定の場合）
  * `outline_color_field::Symbol = :null`: 点のアウトラインの色付けに使用する `table` の列の名前
  * `outline_color_range = [colorant"#FFFFFF", colorant"#000000"]`: アウトライン用の `Colors.jl` 互換の色のベクトル。生成するには `colorant"xyz"` を使用します。
  * `outline_color_scale = "quantile"`: アウトラインカラーに値または分位数が使用されるべきかに応じて、`"quantize"` または `"quantile"` のいずれか。
  * `outline_width_field::Symbol = :null`: ポリゴンアウトラインの幅を決定するために使用される `table` の列の名前
  * `outline_width_scale = "linear"`: `outline_width_field` の値がアウトラインの幅にどのように変換されるべきか
  * `height_field::Symbol = :null`: フィーチャの高さを決定するために使用される `table` の列の名前
  * `height_scale = "linear"`: `height_field` が実際の高さにどのように変換されるべきか
  * `elevation_scale = 1.0`: 高さのスケーリングファクター
  * `enable_elevation_zoom_factor = true`
  * `enable_3d = false`: レイヤーで3Dを有効にする

# 例

```julia
m = KeplerGL.KeplerGLMap(token, center_map=false, read_only=true)
df = CSV.read("assets/example_data/counties-unemployment.csv", DataFrame)
KeplerGL.add_polygon_layer!(m, df, :_geojson ,
    color = colorant"red", color_field = :unemployment_rate, color_range = ColorBrewer.palette("RdPu", 9),
    color_scale = "quantile", opacity = 0.8)
```
