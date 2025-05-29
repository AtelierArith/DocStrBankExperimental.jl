```
express(obj, repr::AbstractRepresentation)
express(obj, repr::AbstractRepresentation, use::AbstractUse)
```

量子オブジェクト `obj` をバックエンド表現 `repr` に変換します。形式特有のケース、例えば `QuantumCliffordRepr` のために `use` を定義することが重要です。
