```
addmodality!(md, indices)
addmodality!(md, index)
addmodality!(md, variable_names)
addmodality!(md, variable_name)
```

Create a new modality in a multimodal dataset using variables at `indices` or `index`, and return the dataset itself.

Alternatively to the `indices` and the `index`, the variable name(s) can be used.

Note: to add a new modality with new variables see [`insertmodality!`](@ref).

# Arguments

  * `md` is a `MultiDataset`;
  * `indices` is an `AbstractVector{Integer}` that indicates which indices of the multimodal   dataset's corresponding dataframe to add to the new modality;
  * `index` is an `Integer` that indicates the index of the multimodal dataset's corresponding   dataframe to add to the new modality;
  * `variable_names` is an `AbstractVector{Symbol}` that indicates which variables of the   multimodal dataset's corresponding dataframe to add to the new modality;
  * `variable_name` is a `Symbol` that indicates the variable of the multimodal dataset's   corresponding dataframe to add to the new modality;

# Examples

```julia-repl
julia> df = DataFrame(:name => ["Python", "Julia"], :age => [25, 26], :sex => ['M', 'F'], :height => [180, 175], :weight => [80, 60])
2×5 DataFrame
 Row │ name    age    sex   height  weight
     │ String  Int64  Char  Int64   Int64
─────┼─────────────────────────────────────
   1 │ Python     25  M        180      80
   2 │ Julia      26  F        175      60

julia> md = MultiDataset([[1]], df)
● MultiDataset
   └─ dimensionalities: (0,)
- Modality 1 / 1
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
- Spare variables
   └─ dimensionality: 0
2×4 SubDataFrame
 Row │ age    sex   height  weight
     │ Int64  Char  Int64   Int64
─────┼─────────────────────────────
   1 │    25  M        180      80
   2 │    26  F        175      60


julia> addmodality!(md, [:age, :sex])
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
 Row │ age    sex
     │ Int64  Char
─────┼─────────────
   1 │    25  M
   2 │    26  F
- Spare variables
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ height  weight
     │ Int64   Int64
─────┼────────────────
   1 │    180      80
   2 │    175      60


julia> addmodality!(md, 5)
● MultiDataset
   └─ dimensionalities: (0, 0, 0)
- Modality 1 / 3
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
- Modality 2 / 3
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ age    sex
     │ Int64  Char
─────┼─────────────
   1 │    25  M
   2 │    26  F
- Modality 3 / 3
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ weight
     │ Int64
─────┼────────
   1 │     80
   2 │     60
- Spare variables
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ height
     │ Int64
─────┼────────
   1 │    180
   2 │    175
```
