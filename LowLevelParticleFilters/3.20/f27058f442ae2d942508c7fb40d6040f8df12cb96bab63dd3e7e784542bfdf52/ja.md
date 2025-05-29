```
RBMeasurementModel{IPM}(measurement, R2, ny)
```

ラオ-ブラックウェル化粒子フィルタのための測定モデル。

# フィールド:

  * `measurement`: 非線形状態から出力への寄与、$g$ は $y = g(x^n, u, p, t) + C x^l + e$ におけるもの
  * `R2`: 測定ノイズの確率分布。`C == 0` の場合、これは任意の分布であり得るが、そうでない場合は `MvNormal` または `SimpleMvNormal` のインスタンスでなければならない。
  * `ny`: 出力の数
