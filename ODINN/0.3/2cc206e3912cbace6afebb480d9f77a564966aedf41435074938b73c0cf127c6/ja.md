```
mutable struct TrainingStats
```

トレーニングの情報を持つオブジェクトです。

# フィールド

  * `retcode`: 最適化の報告コード。
  * `losses`: 各イテレーションでの損失関数の値を格納するベクター。
  * `niter`: 総イテレーション/エポック数。
  * `θ`: トレーニング後のニューラルネットワークのパラメータ。
