```
asymptote_export_SPD(filename)
```

与えられた `data` を、対称正定値行列のマニフォールド上の1次元、2次元、または3次元データの点として `Power(SymmetricPositiveDefinnite(3))` にエクスポートします。

# 入力

  * `filename`        Asymptote コードを保存するファイル。

# データのオプション引数

  * `data`            SPD 行列の1D、2D、または3D配列を表す点
  * `color_scheme`    幾何学的異方性指数のための `ColorScheme`
  * `scale_axes`:      （`(1/3,1/3,1/3)`）対称正定値行列を、関与するすべてのSPD点の最大固有値によって推定される距離に比べて、各方向ごとにファクターで近づけます。

# Asymptote のオプション引数

  * `camera_position`  カメラシーンの位置（デフォルト：データのxy平面の中心の上）
  * `target`           カメラが向く位置（デフォルト：データ内のxy平面の中心）。

`camera_position` と `target` の両方の値は `scaledAxes*EW` によってスケーリングされ、ここで `EW` は `data` の最大固有値です。
