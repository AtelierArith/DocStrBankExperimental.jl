```
dropmodalities!(md, indices)
dropmodalities!(md, index)
```

Remove the `i`-th modality from a multimodal dataset while dropping all variables in it, and return the dataset itself.

Note: if the dropped variables are contained in other modalities they will also be removed from them. This can lead to the removal of additional modalities other than the `i`-th.

If the intention is to remove a modality without dropping the variables use [`removemodality!`](@ref) instead.

# Arguments

  * `md` is a `MultiDataset`;
  * `index` is an `Integer` indicating the index of the modality to drop;
  * `indices` is an `AbstractVector{Integer}` indicating the indices of the modalities to drop.

# Examples

```julia-repl
julia> df = DataFrame(:name => ["Python", "Julia"], :age => [25, 26], :sex => ['M', 'F'], :height => [180, 175], :weight => [80, 60])
2×5 DataFrame
 Row │ name    age    sex   height  weight
     │ String  Int64  Char  Int64   Int64
─────┼─────────────────────────────────────
   1 │ Python     25  M        180      80
   2 │ Julia      26  F        175      60

julia> md = MultiDataset([[1, 2],[3,4],[5],[2,3]], df)
● MultiDataset
   └─ dimensionalities: (0, 0, 0, 0)
- Modality 1 / 4
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ name    age
     │ String  Int64
─────┼───────────────
   1 │ Python     25
   2 │ Julia      26
- Modality 2 / 4
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ sex   height
     │ Char  Int64
─────┼──────────────
   1 │ M        180
   2 │ F        175
- Modality 3 / 4
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ weight
     │ Int64
─────┼────────
   1 │     80
   2 │     60
- Modality 4 / 4
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ age    sex
     │ Int64  Char
─────┼─────────────
   1 │    25  M
   2 │    26  F

julia> dropmodalities!(md, [2,3])
[ Info: Variable 3 was last variable of modality 2: removing modality
[ Info: Variable 3 was last variable of modality 2: removing modality
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
 Row │ age
     │ Int64
─────┼───────
   1 │    25
   2 │    26

julia> dropmodalities!(md, 2)
[ Info: Variable 2 was last variable of modality 2: removing modality
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
```
