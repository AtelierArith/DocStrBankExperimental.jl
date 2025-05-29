```
dropvariables!(md, i)
dropvariables!(md, variable_name)
dropvariables!(md, indices)
dropvariables!(md, variable_names)
dropvariables!(md, i_modality, indices)
dropvariables!(md, i_modality, variable_names)
```

`i`-番目の変数をマルチモーダルデータセットから削除し、データセット自体を返します。

# 引数

  * `md` は MultiDataset です;
  * `i` は削除する変数のインデックスを示す `Integer` です;
  * `variable_name` は削除する変数を示す `Symbol` です;
  * `indices` は削除する変数のインデックスを示す `AbstractVector{Integer}` です;
  * `variable_names` は削除する変数を示す `AbstractVector{Symbol}` です;
  * `i_modality`: モダリティのインデックス; この引数が指定されている場合、`indices` は `i_modality`-番目のモダリティに対して相対的に考慮されます

# 例

```julia-repl
julia> md = MultiDataset([[1, 2],[3, 4, 5]], DataFrame(:name => ["Python", "Julia"], :age => [25, 26], :sex => ['M', 'F'], :height => [180, 175], :weight => [80, 60]))
● MultiDataset
   └─ dimensionalities: (0, 0)
- Modality 1 / 2
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ name    age
     │ String  Int64
─────┼───────────────
   1 │ Python     25
   2 │ Julia      26
- Modality 2 / 2
   └─ dimensionality: 0
2×3 SubDataFrame
 Row │ sex   height  weight
     │ Char  Int64   Int64
─────┼──────────────────────
   1 │ M        180      80
   2 │ F        175      60

julia> dropvariables!(md, 4)
● MultiDataset
   └─ dimensionalities: (0, 0)
- Modality 1 / 2
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ name    age
     │ String  Int64
─────┼───────────────
   1 │ Python     25
   2 │ Julia      26
- Modality 2 / 2
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ sex   weight
     │ Char  Int64
─────┼──────────────
   1 │ M         80
   2 │ F         60

julia> dropvariables!(md, :name)
● MultiDataset
   └─ dimensionalities: (0, 0)
- Modality 1 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    25
   2 │    26
- Modality 2 / 2
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ sex   weight
     │ Char  Int64
─────┼──────────────
   1 │ M         80
   2 │ F         60

julia> dropvariables!(md, [1,3])
[ Info: 変数 1 はモダリティ 1 の最後の変数でした: モダリティを削除しています
● MultiDataset
   └─ dimensionalities: (0,)
- Modality 1 / 1
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F
```

TODO: レビューが必要です
