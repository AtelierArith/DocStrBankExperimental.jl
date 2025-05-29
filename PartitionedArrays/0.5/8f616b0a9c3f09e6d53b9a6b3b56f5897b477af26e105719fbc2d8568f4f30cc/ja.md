```
struct LocalIndices
```

任意のローカルインデックスのコンテナ。

# プロパティ

  * `n_global::Int`: グローバルインデックスの数。
  * `owner::Int32`: ローカルインデックスを格納する部分のID
  * `local_to_global::Vector{Int}`: この部分のローカルインデックスのグローバルID。 `local_to_global[i_local]`はローカルインデックス番号`i_local`に対応するグローバルIDです。
  * `local_to_owner::Vector{Int32}`: ローカルIDの所有者。 `local_to_owner[i_local]`はローカルインデックス番号`i_local`の所有者のIDです。

# スーパタイプ階層

```
LocalIndices <: AbstractLocalIndices
```
