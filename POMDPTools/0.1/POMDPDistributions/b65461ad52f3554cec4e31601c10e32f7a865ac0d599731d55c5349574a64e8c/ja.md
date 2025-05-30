```
SparseCat(values, probabilities)
```

スパースカテゴリカル分布を作成します。

`values` は、分布内の非ゼロ確率を持つ可能な値を含む反復可能なオブジェクトです（任意の型で構いません）。`probabilities` は、関連する確率を含む反復可能なオブジェクトです。

これは、`weighted_iterator` の高速な実装を使用して値の反復に最適化されています。`pdf` と `rand` はどちらもオーダー n です。
