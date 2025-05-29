```
keeponlyvariables!(md, indices)
keeponlyvariables!(md, variable_names)
```

`indices` にあるインデックスに対応しないすべての変数をマルチモーダルデータセットから削除します。

注意: 削除された変数がいくつかのモダリティに含まれている場合、それらも削除されます。この副作用により、モダリティが削除されることがあります。

# 引数

  * `md` は `MultiDataset` です;
  * `indices` はマルチモーダルデータセットで保持するインデックスを示す `AbstractVector{Integer}` です;
  * `variable_names` はマルチモーダルデータセットで保持する変数を示す `AbstractVector{Symbol}` です。

# 例

```julia-repl
julia> md = MultiDataset([[1, 2],[3, 4, 5],[5]], DataFrame(:name => ["Python", "Julia"], :age => [25, 26], :sex => ['M', 'F'], :height => [180, 175], :weight => [80, 60]))
● MultiDataset
   └─ dimensionalities: (0, 0, 0)
- Modality 1 / 3
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ name    age
     │ String  Int64
─────┼───────────────
   1 │ Python     25
   2 │ Julia      26
- Modality 2 / 3
   └─ dimensionality: 0
2×3 SubDataFrame
 Row │ sex   height  weight
     │ Char  Int64   Int64
─────┼──────────────────────
   1 │ M        180      80
   2 │ F        175      60
- Modality 3 / 3
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ weight
     │ Int64
─────┼────────
   1 │     80
   2 │     60

julia> keeponlyvariables!(md, [1,3,4])
[ Info: 変数 5 はモダリティ 3 の最後の変数でした: モダリティを削除します
● MultiDataset
   └─ dimensionalities: (0, 0)
- Modality 1 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
- Modality 2 / 2
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ sex   height
     │ Char  Int64
─────┼──────────────
   1 │ M        180
   2 │ F        175

julia> keeponlyvariables!(md, [:name, :sex])
● MultiDataset
   └─ dimensionalities: (0, 0)
- Modality 1 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
- Modality 2 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F
```

TODO: レビュー
