```
insertmodality!(md, col, new_modality, existing_variables)
insertmodality!(md, new_modality, existing_variables)
```

Insert `new_modality` as new modality to multimodal dataset, and return the dataset. Existing variables can be added to the new modality while adding it to the dataset by passing the corresponding indices as `existing_variables`. If `col` is specified then the variables will be inserted starting at index `col`.

# Arguments

  * `md` is a `MultiDataset`;
  * `col` is an `Integer` indicating the column in which to insert the columns of   `new_modality`;
  * `new_modality` is an `AbstractDataFrame` which will be added to the multimodal dataset as a   sub-dataframe of a new modality;
  * `existing_variables` is an `AbstractVector{Integer}` or `AbstractVector{Symbol}`. It   indicates which variables of the multimodal dataset internal dataframe structure   to insert in the new modality.

# Examples

```julia-repl
julia> df = DataFrame(
           :name => ["Python", "Julia"],
           :stat1 => [[sin(i) for i in 1:50000], [cos(i) for i in 1:50000]]
       )
2×2 DataFrame
 Row │ name    stat1
     │ String  Array…
─────┼───────────────────────────────────────────
   1 │ Python  [0.841471, 0.909297, 0.14112, -0…
   2 │ Julia   [0.540302, -0.416147, -0.989992,…

julia> md = MultiDataset(df; group = :all)
● MultiDataset
   └─ dimensionalities: (0, 1)
- Modality 1 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
- Modality 2 / 2
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat1
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…

julia> insertmodality!(md, DataFrame(:age => [30, 9]))
● MultiDataset
   └─ dimensionalities: (0, 1, 0)
- Modality 1 / 3
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
- Modality 2 / 3
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat1
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…
- Modality 3 / 3
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    30
   2 │     9

julia> md.data
2×3 DataFrame
 Row │ name    stat1                              age
     │ String  Array…                             Int64
─────┼──────────────────────────────────────────────────
   1 │ Python  [0.841471, 0.909297, 0.14112, -0…     30
   2 │ Julia   [0.540302, -0.416147, -0.989992,…      9
```

or, selecting the column

```julia-repl
julia> df = DataFrame(
           :name => ["Python", "Julia"],
           :stat1 => [[sin(i) for i in 1:50000], [cos(i) for i in 1:50000]]
       )
2×2 DataFrame
 Row │ name    stat1
     │ String  Array…
─────┼───────────────────────────────────────────
   1 │ Python  [0.841471, 0.909297, 0.14112, -0…
   2 │ Julia   [0.540302, -0.416147, -0.989992,…

julia> md = MultiDataset(df; group = :all)
● MultiDataset
   └─ dimensionalities: (0, 1)
- Modality 1 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
- Modality 2 / 2
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat1
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…

julia> insertmodality!(md, 2, DataFrame(:age => [30, 9]))
● MultiDataset
   └─ dimensionalities: (1, 0)
- Modality 1 / 2
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat1
     │ Array…
─────┼───────────────────────────────────
    1 │ [0.841471, 0.909297, 0.14112, -0…
    2 │ [0.540302, -0.416147, -0.989992,…
- Modality 2 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    30
   2 │     9
- Spare variables
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia

julia> md.data
2×3 DataFrame
 Row │ name    age    stat1
     │ String  Int64  Array…
─────┼──────────────────────────────────────────────────
   1 │ Python     30  [0.841471, 0.909297, 0.14112, -0…
   2 │ Julia       9  [0.540302, -0.416147, -0.989992,…
```

or, adding an existing variable:

```julia-repl
julia> df = DataFrame(
           :name => ["Python", "Julia"],
           :stat1 => [[sin(i) for i in 1:50000], [cos(i) for i in 1:50000]]
       )
2×2 DataFrame
 Row │ name    stat1
     │ String  Array…
─────┼───────────────────────────────────────────
   1 │ Python  [0.841471, 0.909297, 0.14112, -0…
   2 │ Julia   [0.540302, -0.416147, -0.989992,…

julia> md = MultiDataset([[2]], df)
● MultiDataset
   └─ dimensionalities: (1,)
- Modality 1 / 1
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat1
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…
- Spare variables
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia


julia> insertmodality!(md, DataFrame(:age => [30, 9]); existing_variables = [1])
● MultiDataset
   └─ dimensionalities: (1, 0)
- Modality 1 / 2
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat1
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…
- Modality 2 / 2
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ age    name
     │ Int64  String
─────┼───────────────
   1 │    30  Python
   2 │     9  Julia
```
