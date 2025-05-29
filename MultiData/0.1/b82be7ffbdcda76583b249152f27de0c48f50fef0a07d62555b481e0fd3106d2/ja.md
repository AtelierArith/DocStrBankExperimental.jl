```
removevariable_frommodality!(md, i_modality, var_indices)
removevariable_frommodality!(md, i_modality, var_index)
removevariable_frommodality!(md, i_modality, var_name)
removevariable_frommodality!(md, i_modality, var_names)
```

インデックス `var_index` の変数を、マルチモーダルデータセットのインデックス `i_modality` のモダリティから削除し、データセット自体を返します。

`var_index` の代わりに変数名を使用することもできます。複数の変数を一度にマルチモーダルデータセットから削除するには、最後の引数として `Symbols` の `Vector`（名前用）または整数の `Vector`（インデックス用）を渡します。

注意: すべての変数がモダリティから削除されると、そのモダリティは削除されます。

# 引数

  * `md` は `MultiDataset` です;
  * `i_modality` は、変数を削除するモダリティを示す `Integer` です;
  * `var_index` は、マルチモーダルデータセットの特定のモダリティから削除する変数のインデックスを示す `Integer` です;
  * `var_indices` は、マルチモーダルデータセットの特定のモダリティから削除する変数のインデックスを示す `AbstractVector{Integer}` です;
  * `var_name` は、マルチモーダルデータセットの特定のモダリティから削除する変数の名前を示す `Symbol` です;
  * `var_names` は、マルチモーダルデータセットの特定のモダリティから削除する変数の名前を示す `AbstractVector{Symbol}` です;

# 例

```julia-repl
julia> df = DataFrame(:name => ["Python", "Julia"],
                      :age => [25, 26],
                      :sex => ['M', 'F'],
                      :height => [180, 175],
                      :weight => [80, 60])
                     )
2×5 DataFrame
 Row │ name    age    sex   height  weight
     │ String  Int64  Char  Int64   Int64
─────┼─────────────────────────────────────
   1 │ Python     25  M        180      80
   2 │ Julia      26  F        175      60

julia> md = MultiDataset([[1,2,4],[2,3,4],[5]], df)
● MultiDataset
   └─ dimensionalities: (0, 0, 0)
- Modality 1 / 3
   └─ dimensionality: 0
2×3 SubDataFrame
 Row │ name    age    height
     │ String  Int64  Int64
─────┼───────────────────────
   1 │ Python     25     180
   2 │ Julia      26     175
- Modality 2 / 3
   └─ dimensionality: 0
2×3 SubDataFrame
 Row │ age    sex   height
     │ Int64  Char  Int64
─────┼─────────────────────
   1 │    25  M        180
   2 │    26  F        175
- Modality 3 / 3
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ weight
     │ Int64
─────┼────────
   1 │     80
   2 │     60

julia> removevariable_frommodality!(md, 3, 5)
[ Info: 変数 5 はモダリティ 3 の最後の変数でした: モダリティを削除します
● MultiDataset
   └─ dimensionalities: (0, 0)
- Modality 1 / 2
   └─ dimensionality: 0
2×3 SubDataFrame
 Row │ name    age    height
     │ String  Int64  Int64
─────┼───────────────────────
   1 │ Python     25     180
   2 │ Julia      26     175
- Modality 2 / 2
   └─ dimensionality: 0
2×3 SubDataFrame
 Row │ age    sex   height
     │ Int64  Char  Int64
─────┼─────────────────────
   1 │    25  M        180
   2 │    26  F        175
- Spare variables
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ weight
     │ Int64
─────┼────────
   1 │     80
   2 │     60

julia> removevariable_frommodality!(md, 1, :age)
● MultiDataset
   └─ dimensionalities: (0, 0)
- Modality 1 / 2
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ name    height
     │ String  Int64
─────┼────────────────
   1 │ Python     180
   2 │ Julia      175
- Modality 2 / 2
   └─ dimensionality: 0
2×3 SubDataFrame
 Row │ age    sex   height
     │ Int64  Char  Int64
─────┼─────────────────────
   1 │    25  M        180
   2 │    26  F        175
- Spare variables
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ weight
     │ Int64
─────┼────────
   1 │     80
   2 │     60

julia> removevariable_frommodality!(md, 2, [3,4])
● MultiDataset
   └─ dimensionalities: (0, 0)
- Modality 1 / 2
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ name    height
     │ String  Int64
─────┼────────────────
   1 │ Python     180
   2 │ Julia      175
- Modality 2 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    25
   2 │    26
- Spare variables
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ sex   weight
     │ Char  Int64
─────┼──────────────
   1 │ M         80
   2 │ F         60

julia> removevariable_frommodality!(md, 1, [:name,:height])
[ Info: 変数 4 はモダリティ 1 の最後の変数でした: モダリティを削除します
● MultiDataset
   └─ dimensionalities: (0,)
- Modality 1 / 1
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    25
   2 │    26
- Spare variables
   └─ dimensionality: 0
2×4 SubDataFrame
 Row │ name    sex   height  weight
     │ String  Char  Int64   Int64
─────┼──────────────────────────────
   1 │ Python  M        180      80
   2 │ Julia   F        175      60
```
