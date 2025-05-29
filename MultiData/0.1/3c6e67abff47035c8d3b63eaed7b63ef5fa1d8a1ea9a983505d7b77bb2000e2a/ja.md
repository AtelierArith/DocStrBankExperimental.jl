```
dropsparevariables!(md)
```

マルチモーダルデータセット内のいずれのモダリティにも含まれていない変数をすべて削除します。

# 引数

  * `md` は `MultiDataset` であり、スパーベリアブルが削除される構造体です。

# 例

```julia-repl
julia> md = MultiDataset([[1]], DataFrame(:age => [30, 9], :name => ["Python", "Julia"]))
● MultiDataset
   └─ 次元数: (0,)
- モダリティ 1 / 1
   └─ 次元数: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    30
   2 │     9
- スパーベリアブル
   └─ 次元数: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia


julia> dropsparevariables!(md)
2×1 DataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
```
