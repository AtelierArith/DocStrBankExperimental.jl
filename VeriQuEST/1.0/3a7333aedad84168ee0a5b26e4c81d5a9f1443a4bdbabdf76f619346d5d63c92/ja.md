```
mutable struct Damping <: NoiseModels
```

単一キュービットのダンピングノイズモデルを表す構造体です。

# フィールド

  * `backend`: シミュレーションに使用されるバックエンド。
  * `type`: ノイズモデルのタイプ（SingleQubit）。
  * `prob`: ダンピングの確率で、単一の値またはベクトルであることができます。
