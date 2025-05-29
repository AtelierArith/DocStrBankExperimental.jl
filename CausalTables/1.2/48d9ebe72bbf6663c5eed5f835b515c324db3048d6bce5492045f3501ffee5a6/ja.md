```
KOrderStatistics <: NetworkSummary
```

隣接 `matrix` における各ユニットの接続された隣人のターゲット変数の上位 K 順序値を計算する NetworkSummary です。

# フィールド

  * `target::Symbol`: `StructuralCausalModel` の `DataGeneratingProcess` で要約されるターゲット変数を示すキー; または、`CausalTable` の `data` 属性で要約されるターゲット変数。
  * `matrix::Symbol`: `StructuralCausalModel` の `DataGeneratingProcess` で要約が計算される隣接行列を示すキー; または、`CausalTable` の `arrays` 属性における隣接行列のキー。
  * `weights::Union{Symbol, Nothing}`: 各ユニットが要約で重み付けされるためのオプションの変数。
