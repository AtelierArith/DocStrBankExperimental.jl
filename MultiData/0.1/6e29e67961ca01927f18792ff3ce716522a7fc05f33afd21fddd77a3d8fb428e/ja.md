```
addvariable_tomodality!(md, i_modality, var_index)
addvariable_tomodality!(md, i_modality, var_indices)
addvariable_tomodality!(md, i_modality, var_name)
addvariable_tomodality!(md, i_modality, var_names)
```

インデックス `var_index` の変数を、マルチモーダルデータセットのインデックス `i_modality` のモダリティに追加し、データセットを返します。`var_index` の代わりに変数名を使用することもできます。複数の変数を `var_indices` または `var_names` を使用してマルチモーダルデータセットに一度に挿入することができます。

注意: この関数は新しいモダリティに変数を追加することは許可されておらず、既存のモダリティにのみ追加することができます。新しいモダリティを追加するには、代わりに [`addmodality!`](@ref) を使用してください。

# 引数

  * `md` は `MultiDataset` です;
  * `i_modality` は、変数を追加するモダリティを示す `Integer` です;
  * `var_index` は、マルチモーダルデータセットの特定のモダリティに追加する変数のインデックスを示す `Integer` です;
  * `var_indices` は、マルチモーダルデータセットの特定のモダリティに追加する変数のインデックスを示す `AbstractVector{Integer}` です;
  * `var_name` は、マルチモーダルデータセットの特定のモダリティに追加する変数の名前を示す `Symbol` です;
  * `var_names` は、マルチモーダルデータセットの特定のモダリティに追加する変数の名前を示す `AbstractVector{Symbol}` です;

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

julia> md = MultiDataset([[1, 2],[3]], df)
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
2×1 SubDataFrame
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F
- Spare variables
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ height  weight
     │ Int64   Int64
─────┼────────────────
   1 │    180      80
   2 │    175      60

julia> addvariable_tomodality!(md, 1, [4,5])
● MultiDataset
   └─ dimensionalities: (0, 0)
- Modality 1 / 2
   └─ dimensionality: 0
2×4 SubDataFrame
 Row │ name    age    height  weight
     │ String  Int64  Int64   Int64
─────┼───────────────────────────────
   1 │ Python     25     180      80
   2 │ Julia      26     175      60
- Modality 2 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F

julia> addvariable_tomodality!(md, 2, [:name,:weight])
● MultiDataset
   └─ dimensionalities: (0, 0)
- Modality 1 / 2
   └─ dimensionality: 0
2×4 SubDataFrame
 Row │ name    age    height  weight
     │ String  Int64  Int64   Int64
─────┼───────────────────────────────
   1 │ Python     25     180      80
   2 │ Julia      26     175      60
- Modality 2 / 2
   └─ dimensionality: 0
2×3 SubDataFrame
 Row │ sex   name    weight
     │ Char  String  Int64
─────┼──────────────────────
   1 │ M     Python      80
   2 │ F     Julia       60
```
