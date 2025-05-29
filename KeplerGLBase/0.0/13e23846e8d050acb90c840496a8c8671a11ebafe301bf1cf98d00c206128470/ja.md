```
add_cluster_layer!(m::KeplerGLMap, table, latitude::Symbol, longitude::Symbol;
    color = colorant"#762A83",
    color_range = [colorant"#762A83",colorant"#AF8DC3",colorant"#E7D4E8",colorant"#D9F0D3",colorant"#7FBF7B",colorant"#1B7837"],
    highlight_color = colorant"#762A83",
    radius_range = [1,40],
    cluster_radius = 20,
    color_aggregation = "count",
    color_field::Symbol = :null,
    color_scale = "quantize",
    opacity = 1.0)
```

地図 `m` にクラスターレイヤーを追加し、`table` からデータを描画します。

# 必須引数

  * `m::KeplerGLMap`: レイヤーを追加する地図
  * `table`: 描画に使用するデータを含む `Tables.jl` 互換のテーブル
  * `latitude::Symbol`: ヘキサビンに集約されるポイントの緯度を含む `table` の列の名前
  * `longitude::Symbol`: ヘキサビンに集約されるポイントの経度を含む `table` の列の名前

# オプション引数

  * `id = randstring(7)`: レイヤーの文字列 ID
  * `color = colorant"#762A83"`: ヘキサゴンが持つべき `Colors.jl` 互換の色（固定の場合）
  * `color_range`: `Colors.jl` 互換の色のベクトル。生成するには `colorant"xyz"` を使用します。
  * `color_field::Symbol = :null`: クラスターポイントの色付けに使用する `table` の列の名前
  * `color_scale = "quantize"`: 色に使用する値または分位数に応じて `"quantize"` または `"quantile"` のいずれか
  * `highlight_color = colorant"#762A83"`: ハイライトカラー。
  * `radius_range = [1,40]`: ポイント半径の範囲
  * `cluster_radius = 20`: クラスタリングの半径
  * `color_aggregation = "count"`: 色の集約方法
  * `opacity = 1.0`: レイヤーの不透明度、`0.0` と `1.0` の間

# 例

```julia
m = KeplerGL.KeplerGLMap(token)
df = CSV.read("assets/example_data/data.csv", DataFrame)
KeplerGL.add_cluster_layer!(m, df, :Latitude, :Longitude, opacity = 0.5, color_field = :Magnitude, color_scale = "quantile",
    radius_range = [1,40], cluster_radius = 20, color_range = ColorBrewer.palette("BuPu",6), color_aggregation = "count" )
```
