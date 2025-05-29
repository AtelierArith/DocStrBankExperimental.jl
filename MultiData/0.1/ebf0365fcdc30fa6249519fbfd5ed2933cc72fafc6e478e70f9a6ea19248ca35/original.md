```
dropvariables!(md, i)
dropvariables!(md, variable_name)
dropvariables!(md, indices)
dropvariables!(md, variable_names)
dropvariables!(md, i_modality, indices)
dropvariables!(md, i_modality, variable_names)
```

Drop the `i`-th variable from a multimodal dataset, and return the dataset itself.

# Arguments

  * `md` is an MultiDataset;
  * `i` is an `Integer` that indicates the index of the variable to drop;
  * `variable_name` is a `Symbol` that idicates the variable to drop;
  * `indices` is an `AbstractVector{Integer}` that indicates the indices of the variables to   drop;
  * `variable_names` is an `AbstractVector{Symbol}` that indicates the variables to drop.
  * `i_modality`: index of the modality; if this argument is specified,   `indices` are considered as relative to the `i_modality`-th modality

# Examples

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
[ Info: Variable 1 was last variable of modality 1: removing modality
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

TODO: To be reviewed
