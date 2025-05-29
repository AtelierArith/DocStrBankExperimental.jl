```
add_point_layer!(m, table, latitude::Symbol, longitude::Symbol;
    color = colorant"#762A83",
    color_field::Symbol = :null,
    color_range = [colorant"#762A83",colorant"#AF8DC3",colorant"#E7D4E8",colorant"#D9F0D3",colorant"#7FBF7B",colorant"#1B7837"],
    color_scale = "quantize",
    highlight_color = colorant"#762A83",
    altitude::Symbol = :null,
    radius = 10.0,
    radius_fixed = true,
    radius_field::Symbol = :null,
    radius_range = [5.0, 15.0],
    radius_scale = "sqrt",
    filled = true,
    opacity = 1.0,
    outline = false,
    outline_thickness = 2.0,
    outline_color = colorant"#000000",
    outline_color_field::Symbol = :null,
    outline_color_range = [colorant"#FFFFFF", colorant"#000000"],
    outline_color_scale = "quantile")

マップ `m` にポイントレイヤーを追加し、`table` からデータを描画します。

# 必須引数

  * `m::KeplerGLMap`: レイヤーを追加するマップ
  * `table`: 描画に使用するデータを含む `Tables.jl` 互換のテーブル
  * `latitude::Symbol`: ポイントの緯度を含む `table` の列の名前
  * `longitude::Symbol`: ポイントの経度を含む `table` の列の名前

# オプション引数

  * `id = randstring(7)`: レイヤーの文字列 ID
  * `color = colorant"#762A83"`: ポイントが持つべき `Colors.jl` 互換の色（固定の場合）
  * `color_field::Symbol = :null`: ポイントの色付けに使用する `table` の列の名前
  * `color_range`: `Colors.jl` 互換の色のベクトル。生成するには `colorant"xyz"` を使用します。
  * `color_scale = "quantize"`: 色に使用する値または分位数に応じて `"quantize"` または `"quantile"` のいずれか。
  * `highlight_color = colorant"#762A83"`: ハイライトカラー。
  * `altitude::Symbol = :null`: ポイントの高度に使用する `table` の列の名前
  * `radius = 10.0`: マップ上のポイントの固定半径値
  * `radius_fixed = true`: 半径が固定されるべきか、`radius_field` に依存するべきか
  * `radius_field::Symbol = :null`: ポイントの半径に使用する `table` の列の名前
  * `radius_range = [5.0, 15.0]`: ポイントの半径の範囲
  * `radius_scale = "sqrt"`: `radius_field` を半径にマッピングする方法
  * `filled = true`: ポイントマーカーが塗りつぶされるべきかどうか
  * `opacity = 1.0`: ポイントの不透明度、`0.0` と `1.0` の間
  * `outline = false`: ポイントマーカーにアウトラインが必要かどうか
  * `outline_thickness = 2.0`: アウトラインの厚さ
  * `outline_color = colorant"#000000"`: ポイントのアウトラインが持つべき `Colors.jl` 互換の色（固定の場合）
  * `outline_color_field::Symbol = :null`: ポイントのアウトラインの色付けに使用する `table` の列の名前
  * `outline_color_range = [colorant"#FFFFFF", colorant"#000000"]`: アウトライン用の `Colors.jl` 互換の色のベクトル。生成するには `colorant"xyz"` を使用します。
  * `outline_color_scale = "quantile"`: アウトラインの色に使用する値または分位数に応じて `"quantize"` または `"quantile"` のいずれか

# 例

```

julia m = KeplerGL.KeplerGLMap(token) df = CSV.read("assets/example*data/data.csv", DataFrame) KeplerGL.add*point*layer!(m, df, :Latitude, :Longitude,     color = colorant"rgb(23,184,190)", color*field = :Magnitude, color*scale = "quantize",     color*range = ColorBrewer.palette("PRGn", 6),     radius*field = :Magnitude, radius*scale = "sqrt", radius*range = [4.2, 96.2], radius*fixed = false,     filled = true, opacity = 0.39, outline = false); ```
