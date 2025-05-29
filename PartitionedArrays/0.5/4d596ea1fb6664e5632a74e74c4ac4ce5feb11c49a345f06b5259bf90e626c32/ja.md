```
struct OwnIndices
```

独自のインデックスのコンテナ。

# プロパティ

  * `n_global::Int`: グローバルインデックスの数
  * `owner::Int32`: これらのインデックスを所有する部分のID
  * `own_to_global::Vector{Int}`: この部分が所有するインデックスのグローバルID。`own_to_global[i_own]`は、独自インデックス番号`i_own`に対応するグローバルIDです。

# スーパタイプ階層

```
OwnIndices <: Any
```
