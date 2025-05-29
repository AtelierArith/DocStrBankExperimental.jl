```julia
fold!(
    design::ExperimentalDesign.PlackettBurman
) -> DataFrames.DataFrame

```

```jldoctest
julia> fold!(PlackettBurman(2))
8×3 DataFrame
 Row │ factor1  factor2  dummy1
     │ Int64    Int64    Int64
─────┼──────────────────────────
   1 │       1        1       1
   2 │       1       -1      -1
   3 │      -1       -1       1
   4 │      -1        1      -1
   5 │      -1       -1      -1
   6 │      -1        1       1
   7 │       1        1      -1
   8 │       1       -1       1

```
