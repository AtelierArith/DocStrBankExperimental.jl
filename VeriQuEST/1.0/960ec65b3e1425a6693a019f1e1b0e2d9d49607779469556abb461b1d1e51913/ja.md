```
struct Dephasing <: NoiseModels
```

脱相ノイズモデルは、脱相エラーによって引き起こされるノイズを表します。

# フィールド

  * `backend`: シミュレーションに使用されるバックエンド。
  * `type`: ノイズの影響を受けるキュービットのタイプ。`SingleQubit`または`TwoQubits`である可能性があります。
  * `prob`: 脱相エラーの確率。単一の値または確率のベクトルである可能性があります。
