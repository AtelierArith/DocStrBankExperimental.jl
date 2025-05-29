```
Sum <: NetworkSummary
```

`StructuralCausalModel` または `CausalTable` の隣接 `matrix` に接続された各ユニットのターゲット変数の値を合計する `NetworkSummary` 

# フィールド

  * `target::Symbol`: `StructuralCausalModel` の `DataGeneratingProcess` で要約されるターゲット変数を示すキー; または、`CausalTable` の `data` 属性で要約されるターゲット変数。
  * `matrix::Symbol`: `StructuralCausalModel` の `DataGeneratingProcess` で要約が計算される隣接行列を示すキー; または、`CausalTable` の `arrays` 属性における隣接行列のキー。
  * `weights::Union{Symbol, Nothing}`: 各ユニットが要約で重み付けされるためのオプションの変数。
