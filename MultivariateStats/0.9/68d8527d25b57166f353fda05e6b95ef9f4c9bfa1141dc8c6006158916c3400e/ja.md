```
predict(M::ICA, x)
```

モデル `M` に基づいて、独立成分を抽出するために `x` を出力空間に変換します。これは、$\mathbf{W}^T (\mathbf{x} - \boldsymbol{\mu})$ です。
