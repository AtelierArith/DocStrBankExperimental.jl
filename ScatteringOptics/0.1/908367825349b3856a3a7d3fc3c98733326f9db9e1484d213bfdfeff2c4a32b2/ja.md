```
refractivephasescreen(sm, im, Vx_km_per_s=0.0, Vy_km_per_s=0.0)
```

画像に対応する屈折位相スクリーンモデルを生成し、散乱平均画像を計算するための抽象型です。

  * `sm <: AbstractScatteringModel`
  * `im <: IntensityMap`
  * `Vx_km_per_s` と `Vy_km_per_s` は移動位相スクリーン用のオプションであり、まだ実装されていません。
