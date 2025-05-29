```
RefractivePhaseScreen(sm, Nx, Ny, dx, dy, Vx_km_per_s=0.0, Vy_km_per_s=0.0)
```

画像に対応する屈折位相スクリーンモデルを生成し、散乱平均画像を計算するための抽象型です。

  * `sm <: AbstractScatteringModel`
  * `Nx`: x軸の画像サイズ
  * `Ny`: y軸の画像サイズ
  * `dx`: x方向のピクセルサイズ（ラジアン単位）
  * `dy`: y方向のピクセルサイズ（ラジアン単位）

`Vx_km_per_s` と `Vy_km_per_s` は移動する位相スクリーンのためのオプションです。
