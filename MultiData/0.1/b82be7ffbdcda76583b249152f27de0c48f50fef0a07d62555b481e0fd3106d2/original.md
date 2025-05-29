```
removevariable_frommodality!(md, i_modality, var_indices)
removevariable_frommodality!(md, i_modality, var_index)
removevariable_frommodality!(md, i_modality, var_name)
removevariable_frommodality!(md, i_modality, var_names)
```

Remove variable at index `var_index` from the modality at index `i_modality` in a multimodal dataset, and return the dataset itself.

Alternatively to `var_index` the variable name can be used. Multiple variables can be dropped from the multimodal dataset at once, by passing a `Vector` of `Symbols` (for names), or a `Vector` of integers (for indices) as a last argument.

Note: when all variables are dropped from a modality, it will be removed.

# Arguments

  * `md` is a `MultiDataset`;
  * `i_modality` is an `Integer` indicating the modality in which the variable(s)   will be dropped;
  * `var_index` is an `Integer` that indicates the index of the variable to drop from a   specific modality of the multimodal dataset;
  * `var_indices` is an `AbstractVector{Integer}` indicating the indices of the variables   to drop from a specific modality of the multimodal dataset;
  * `var_name` is a `Symbol` indicating the name of the variable to drop from a specific   modality of the multimodal dataset;
  * `var_names` is an `AbstractVector{Symbol}` indicating the name of the variables to   drop from a specific modality of the multimodal dataset;

# Examples

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
[ Info: Variable 5 was last variable of modality 3: removing modality
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
[ Info: Variable 4 was last variable of modality 1: removing modality
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
