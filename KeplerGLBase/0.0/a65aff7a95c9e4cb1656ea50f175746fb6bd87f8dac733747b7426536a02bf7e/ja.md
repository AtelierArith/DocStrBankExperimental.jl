```
add_trip_layer!(m::KeplerGLMap, table, geojson::Symbol;
m::KeplerGLMap, table, geojson::Symbol;
id::String = randstring(7),
color = colorant"#762A83",
color_field::Symbol = :null,
color_range = [colorant"#762A83",colorant"#AF8DC3",colorant"#E7D4E8",colorant"#D9F0D3",colorant"#7FBF7B",colorant"#1B7837"],
color_scale = "quantize",
highlight_color = colorant"#762A83",
trail_length = 180,
opacity = 1.0,
outline_thickness = 2.0,
outline_width_field::Symbol = :null,
outline_width_scale = "linear",
outline_width_range = [0,10])
```

地図 `m` にポリゴンレイヤーを追加し、`table` からデータを描画します。

# 必須引数

  * `m::KeplerGLMap`: レイヤーを追加する地図
  * `table`: 描画に使用するデータを含む `Tables.jl` 互換のテーブル
  * `geojson::Symbol`: `table` の中で GeoJSON 形式（`LineString` として、[こちら](https://docs.kepler.gl/docs/user-guides/c-types-of-layers/k-trip)を参照）でトリップを含む列の名前

# オプション引数

  * `id = randstring(7)`: レイヤーの文字列 ID
  * `color = colorant"#762A83"`: 形状が持つべき `Colors.jl` 互換の色（固定の場合）
  * `color_field::Symbol = :null`: 形状の色付けに使用する `table` の列の名前
  * `color_range`: `Colors.jl` 互換の色のベクトル。生成するには `colorant"xyz"` を使用します。
  * `color_scale = "quantize"`: 値または分位数が色に使用されるべきかに応じて、`"quantize"` または `"quantile"` のいずれか。
  * `highlight_color = colorant"#762A83"`: ハイライトカラー。
  * `trail_length = 180`: パスがフェードアウトするのにかかる秒数。
  * `opacity = 1.0`: ポイントの不透明度、`0.0` と `1.0` の間
  * `outline_thickness = 2.0`: アウトラインの厚さ
  * `outline_width_field::Symbol = :null`: ポリゴンのアウトラインの幅を決定するために使用される `table` の列の名前
  * `outline_width_scale = "linear"`: `outline_width_field` の値がアウトラインの幅にどのように変換されるべきか

!!! note
    トリップレイヤーはトリップの動的な視覚化を示しているため、地図を静的な画像としてエクスポートすることはあまり意味がありません。


# 例

```julia
using JSON3
t = JSON3.read("assets/example_data/trip_example.geojson")
df = DataFrame(:geometry => string.(t[:features]))
m = KeplerGL.KeplerGLMap(token)
KeplerGL.add_trip_layer!(m, df, :geometry ,
    id = "abc", color = colorant"red")
KeplerGL.render(m)
```
