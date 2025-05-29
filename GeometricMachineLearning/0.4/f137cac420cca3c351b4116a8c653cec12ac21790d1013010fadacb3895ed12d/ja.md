```
metric(Y::GrassmannManifold, Δ₁::AbstractMatrix, Δ₂::AbstractMatrix)
```

ベクトル `Δ₁` と `Δ₂` のメトリックを `Y` で計算します。

グラスマン多様体の表現は *シュティーフェル多様体の商空間* として実現されます。

グラスマン多様体のメトリックは次のようになります：

$$
g^{Gr}_Y(\Delta_1, \Delta_2) = g^{St}_Y(\Delta_1, \Delta_2) = \mathrm{Tr}(\Delta_1^T (\mathbb{I} - Y Y^T) \Delta_2) = \mathrm{Tr}(\Delta_1^T \Delta_2),
$$

ここで、$Y^T\Delta_i$ を $i = 1, 2$ の場合に使用しました。
