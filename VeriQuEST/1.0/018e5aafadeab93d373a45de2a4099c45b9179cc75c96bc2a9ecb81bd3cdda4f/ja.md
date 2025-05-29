```
mutable struct MixtureDensityMatrices <: NoiseModels
```

密度行列のノイズモデルの混合を表す可変構造体です。

# フィールド

  * `backend`: ノイズモデルに使用されるバックエンド。
  * `type`: 密度行列のタイプ。
  * `prob`: 混合の確率分布。
