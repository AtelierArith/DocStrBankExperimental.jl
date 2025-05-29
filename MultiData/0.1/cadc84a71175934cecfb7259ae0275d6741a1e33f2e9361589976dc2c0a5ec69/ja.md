```
sparevariables(md)
```

マルチモーダルデータセットの任意のモダリティに含まれていないすべての変数のインデックスを返します。

# 引数

  * `md` は `MultiDataset` であり、スパー変数のインデックスを知りたい構造体です。

# 例

```julia-repl
julia> md = MultiDataset([[1],[3]], DataFrame(:name => ["Python", "Julia"], :age => [25, 26], :sex => ['M', 'F']))
● MultiDataset
   └─ 次元数: (0, 0)
- モダリティ 1 / 2
   └─ 次元数: 0
2×1 サブデータフレーム
 行 │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
- モダリティ 2 / 2
   └─ 次元数: 0
2×1 サブデータフレーム
 行 │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F
- スパー変数
   └─ 次元数: 0
2×1 サブデータフレーム
 行 │ age
     │ Int64
─────┼───────
   1 │    25
   2 │    26

julia> md.data
2×3 データフレーム
 行 │ name    age    sex
     │ String  Int64  Char
─────┼─────────────────────
   1 │ Python     25  M
   2 │ Julia      26  F

julia> sparevariables(md)
1-element Vector{Int64}:
 2
```
