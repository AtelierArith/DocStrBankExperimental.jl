```
add_heatmap_layer!(m::KeplerGLMap, table, latitude::Symbol, longitude::Symbol;
    color = colorant"#762A83",
    color_range = [colorant"#762A83",colorant"#AF8DC3",colorant"#E7D4E8",colorant"#D9F0D3",colorant"#7FBF7B",colorant"#1B7837"],
    weight_field::Symbol = :null,
    weight_scale = "linear",
    highlight_color = colorant"#762A83",
    radius = 0.6,
    opacity = 1.0)
```

地図 `m` にヒートマップレイヤーを追加し、`table` からデータを描画します。

# 必須引数

  * `m::KeplerGLMap`: レイヤーを追加する地図
  * `table`: 描画に使用するデータを含む `Tables.jl` 互換のテーブル
  * `latitude::Symbol`: ヘクスビンに集約されるポイントの緯度を含む `table` の列の名前
  * `longitude::Symbol`: ヘクスビンに集約されるポイントの経度を含む `table` の列の名前

# オプション引数

  * `id = randstring(7)`: レイヤーの文字列 ID
  * `color = colorant"#762A83"`: ヘクサゴンが持つべき `Colors.jl` 互換の色（固定の場合）
  * `color_range`: `Colors.jl` 互換の色のベクトル。生成するには `colorant"xyz"` を使用します。
  * `weight_field::Symbol = :null`: ヒートマップの重み付けに使用される `table` の列の名前
  * `weight_scale = "linear"`: `weight_field` を重みに変換する方法
  * `highlight_color = colorant"#762A83"`: ハイライトカラー。
  * `radius = 10.0`: ヒートマップのカーネル幅
  * `opacity = 1.0`: レイヤーの不透明度、`0.0` と `1.0` の間

# 例

```julia
m = KeplerGL.KeplerGLMap(token)
df = CSV.read("assets/example_data/data.csv", DataFrame)
KeplerGL.add_heatmap_layer!(m, df, :Latitude, :Longitude, opacity = 0.5, weight_field = :Magnitude, weight_scale = "linear",
    radius = 20.0, color_range = ColorBrewer.palette("BuPu",6) )
```
