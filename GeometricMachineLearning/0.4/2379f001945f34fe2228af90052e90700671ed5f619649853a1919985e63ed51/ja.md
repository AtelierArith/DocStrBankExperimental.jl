```
metric(Y::StiefelManifold, Δ₁::AbstractMatrix, Δ₂::AbstractMatrix)
```

`Δ₁`と`Δ₂`の点積を`Y`で計算します。

これは、Stiefel多様体の標準リーマン計量を使用します：

$$
g_Y: (\Delta_1, \Delta_2) \mapsto \mathrm{Tr}(\Delta_1^T(\mathbb{I} - \frac{1}{2}YY^T)\Delta_2).
$$
