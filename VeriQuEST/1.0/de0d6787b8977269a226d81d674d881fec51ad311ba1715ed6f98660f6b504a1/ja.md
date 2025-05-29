```
struct Kraus <: NoiseModels
```

Kraus演算子を使用したノイズモデルを表す構造体です。

# フィールド

  * `backend`: ノイズモデルに使用されるバックエンド。
  * `type`: ノイズモデルのタイプで、`SingleQubit`、`TwoQubits`、または`MultipleQubits`のいずれかです。
