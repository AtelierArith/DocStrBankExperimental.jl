```
asymptote_export_S2_data(filename)
```

与えられた `data` を2次元球面上の点の配列としてエクスポートします。これは、[Sphere](https://juliamanifolds.github.io/Manifolds.jl/stable/manifolds/sphere.html) $\mathbb S^2$ 上の点を持つ1次元、2次元、または3次元のデータである可能性があります。

# 入力

  * `filename`                Asymptoteコードを保存するファイル。

# データのオプション引数

  * `data`                    1D、2D、または3Dの点の配列を表す点
  * `elevation_color_scheme`  高度のための `ColorScheme`
  * `scale_axes=(1/3,1/3,1/3)`: 各方向ごとに球を近づけるための係数

# Asymptoteのオプション引数

  * `arrow_head_size=1.8`: ベクトルの矢印のサイズ（mm単位）
  * `camera_position`  カメラシーンの位置（デフォルト：データの中心の上、xy平面上）
  * `target`           カメラが向く位置（デフォルト：データ内のxy平面の中心）。
