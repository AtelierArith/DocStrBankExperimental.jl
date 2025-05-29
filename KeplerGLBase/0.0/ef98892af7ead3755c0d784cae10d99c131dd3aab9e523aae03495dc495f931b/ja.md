```
add_arc_layer!(m::KeplerGLMap, table, latitude0::Symbol, longitude0::Symbol,
    latitude1::Symbol, longitude1::Symbol;
    color = colorant"#762A83",
    color_field::Symbol = :null,
    color_range = [colorant"#762A83",colorant"#AF8DC3",colorant"#E7D4E8",colorant"#D9F0D3",colorant"#7FBF7B",colorant"#1B7837"],
    color_scale = "quantize",
    highlight_color = colorant"#762A83",
    altitude0::Symbol = :null,
    altitude1::Symbol = :null,
    size_field::Symbol = :null,
    size_range = [1,10],
    size_scale = "linear",
    opacity = 1.0,
    thickness = 2.0,
    elevation_scale = 1)

マップ `m` にアークレイヤーを追加し、`table` からデータを描画します。

# 必須引数

  * `m::KeplerGLMap`: レイヤーを追加するマップ
  * `table`: 描画に使用するデータを含む `Tables.jl` 互換のテーブル
  * `latitude0::Symbol`: 線の始点の緯度を含む `table` の列の名前
  * `longitude0::Symbol`: 線の始点の経度を含む `table` の列の名前
  * `latitude1::Symbol`: 線の終点の緯度を含む `table` の列の名前
  * `longitude1::Symbol`: 線の終点の経度を含む `table` の列の名前

# オプション引数

  * `id = randstring(7)`: レイヤーの文字列ID
  * `color = colorant"#762A83"`: 線が持つべき `Colors.jl` 互換の色（固定の場合）
  * `color_field::Symbol = :null`: 線の色付けに使用する `table` の列の名前
  * `color_range = [colorant"#762A83",colorant"#AF8DC3",colorant"#E7D4E8",colorant"#D9F0D3",colorant"#7FBF7B",colorant"#1B7837"]`: `Colors.jl` 互換の色のベクトル。`colorant"xyz"` を使用して生成します。
  * `color_scale = "quantize"`: 値または分位数に基づいて色を使用するかどうかに応じて、`"quantize"` または `"quantile"` のいずれか。
  * `highlight_color = colorant"#762A83"`: ハイライト色。
  * `altitude0::Symbol = :null`: 線の始点の高度。
  * `altitude1::Symbol = :null`: 線の終点の高度。
  * `size_field::Symbol = :null`: 線の太さに使用する `table` の列の名前
  * `size_range = [1,10]`: 線の太さの範囲
  * `size_scale = "linear"`: `size_field` を実際の線の太さに変換する方法
  * `opacity = 1.0`: 線の不透明度
  * `thickness = 2.0`: 定数の場合の線の太さ
  * `elevation_scale = 1`: 高度のスケーリング係数。

# 例

```

julia m = KeplerGL.KeplerGLMap(token, center*map=false) df = CSV.read("assets/example*data/data.csv", DataFrame) df.Latitude1 = df.Latitude .+ (rand(rng, Float64, length(df.Latitude)) .- 0.5) df.Longitude1 = df.Longitude .+ 10.0 .* (rand(rng, Float64, length(df.Longitude)) .- 0.5) KeplerGL.add*arc*layer!(m, df, :Latitude, :Longitude, :Latitude1, :Longitude1,     opacity = 0.5, color*field = :Magnitude, color*scale = "quantile",     color_range = ColorBrewer.palette("BuPu",6), thickness = 3) ```
