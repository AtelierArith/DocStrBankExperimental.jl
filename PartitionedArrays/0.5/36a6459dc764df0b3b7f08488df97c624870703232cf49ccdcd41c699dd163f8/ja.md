```
struct GhostIndices
```

ゴーストインデックスのコンテナ。

# プロパティ

  * `n_global::Int`: グローバルインデックスの数
  * `ghost_to_global::Vector{Int}`: この部分のゴーストインデックスのグローバルID。`ghost_to_global[i_ghost]`は、ゴーストインデックス番号`i_ghost`に対応するグローバルIDです。
  * `ghost_to_owner::Vector{Int32}`: ゴーストIDの所有者。`ghost_to_owner[i_ghost]`は、ゴーストインデックス番号`i_ghost`の所有者のIDです。

# スーパタイプ階層

```
GhostIndices <: Any
```
