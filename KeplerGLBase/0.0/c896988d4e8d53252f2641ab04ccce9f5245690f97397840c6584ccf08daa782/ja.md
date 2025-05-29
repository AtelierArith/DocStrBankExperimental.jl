```
add_icon_layer!(m, table, latitude::Symbol, longitude::Symbol, icon::Symbol;
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
    opacity = 1.0)
```

地図 `m` にアイコンレイヤーを追加し、`table` からデータを描画します。

# 必須引数

  * `m::KeplerGLMap`: レイヤーを追加する地図
  * `table`: 描画に使用するデータを含む `Tables.jl` 互換のテーブル
  * `latitude::Symbol`: ポイントの緯度を含む `table` の列の名前
  * `longitude::Symbol`: ポイントの経度を含む `table` の列の名前
  * `icon::Symbol`: シンボル名の文字列を含む `table` の列の名前。以下に有効なシンボル名のリストがあります。

# オプション引数

  * `id = randstring(7)`: レイヤーの文字列 ID
  * `color = colorant"#762A83"`: ポイントが持つべき `Colors.jl` 互換の色（固定の場合）
  * `color_field::Symbol = :null`: ポイントの色付けに使用する `table` の列の名前
  * `color_range`: `Colors.jl` 互換の色のベクトル。`colorant"xyz"` を使用して生成します。
  * `color_scale = "quantize"`: 値または分位数が色に使用されるべきかに応じて、`"quantize"` または `"quantile"` のいずれか。
  * `highlight_color = colorant"#762A83"`: ハイライトカラー。
  * `altitude::Symbol = :null`: ポイントの高度に使用する `table` の列の名前
  * `radius = 10.0`: 地図上のポイントの固定半径値
  * `radius_fixed = true`: 半径が固定されるべきか、`radius_field` に依存するべきか
  * `radius_field::Symbol = :null`: ポイントの半径に使用する `table` の列の名前
  * `radius_range = [5.0, 15.0]`: ポイントの半径の範囲
  * `radius_scale = "sqrt"`: `radius_field` を半径にマッピングする方法
  * `opacity = 1.0`: ポイントの不透明度、`0.0` と `1.0` の間

# 例

```julia
using Random, Colors
m = KeplerGL.KeplerGLMap(token)
df = CSV.read("assets/example_data/data.csv", DataFrame)
rng = MersenneTwister(12345)
df.icon = rand(rng, ["circle", "plus", "delete"], length(df.Latitude))
KeplerGL.add_icon_layer!(m, df, :Latitude, :Longitude, :icon; color = colorant"black");
```
