```
abstract type Accumulating <: StorageBehavior
```

`Accumulating` は、蓄積ストレージレベルのスーパタイプです。

蓄積ストレージの振る舞いは、戦略的な期間における全体のストレージレベルの変化が正または負の両方である可能性があることを意味します。

`Accumulating` の潜在的な使用例には、CO₂が永久に貯蔵されるCO₂貯蔵施設や、複数年の水力発電用貯水池があります。
