```
addvariable_tomodality!(md, i_modality, var_index)
addvariable_tomodality!(md, i_modality, var_indices)
addvariable_tomodality!(md, i_modality, var_name)
addvariable_tomodality!(md, i_modality, var_names)
```

Add variable at index `var_index` to the modality at index `i_modality` in a multimodal dataset, and return the dataset. Alternatively to `var_index` the variable name can be used. Multiple variables can be inserted into the multimodal dataset at once using `var_indices` or `var_inames`.

Note: The function does not allow you to add a variable to a new modality, but only to add it to an existing modality. To add a new modality use [`addmodality!`](@ref) instead.

# Arguments

  * `md` is a `MultiDataset`;
  * `i_modality` is an `Integer` indicating the modality in which the variable(s)   will be added;
  * `var_index` is an `Integer` that indicates the index of the variable to add to a specific   modality of the multimodal dataset;
  * `var_indices` is an `AbstractVector{Integer}` indicating the indices of the variables   to add to a specific modality of the multimodal dataset;
  * `var_name` is a `Symbol` indicating the name of the variable to add to a specific   modality of the multimodal dataset;
  * `var_names` is an `AbstractVector{Symbol}` indicating the name of the variables to   add to a specific modality of the multimodal dataset;

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
