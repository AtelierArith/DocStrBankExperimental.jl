```
ClipScale(ϵ = 1e-5)
```

`MvLocationScale` または `MvLocationScaleLowRank` が `ϵ` より大きい固有値を持つスケールを持つことを保証する射影演算子です。 `ClipScale` は、`Bijectors.TransformedDistribution` オブジェクトでラップされた `MvLocationScale` および `MvLocationScaleLowRank` に対しても操作することをサポートしています。
