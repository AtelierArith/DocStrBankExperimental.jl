```
mutable struct Depolarising <: NoiseModels
```

脱極化ノイズモデルを表す構造体です。

# フィールド

  * `backend`: ノイズモデルに使用されるバックエンド。
  * `type`: ノイズモデルの影響を受けるキュービットのタイプ。
  * `prob`: 脱極化の確率で、単一の値またはベクトルであることができます。
