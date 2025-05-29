```
createcliffordmap(gate_relations::Dict)
```

ゲート関係の辞書からクリフォードゲートマップを作成し、それをグローバルな `clifford_map` にプッシュできます。`gate_relations` は、記号に対するクリフォードゲートの作用を説明するペアを持つ辞書で、例えば `(:X, :X) => (:Z, :X, -1)` のようになります（符号の変更を含む）。
