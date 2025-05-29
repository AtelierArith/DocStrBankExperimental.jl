```julia
RandomLHCDesign(
    n::Int64,
    factors::Tuple
) -> ExperimentalDesign.RandomLHCDesign

```

```jldoctest
julia> RandomLHCDesign(4,Tuple((:A,:B,:C)))
RandomLHCDesign
Dimension: (4, 3)
Factors: (:A, :B, :C)
Design Matrix:
4×3 DataFrame
 Row │ A      B      C
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      4      4
   2 │     2      1      2
   3 │     3      3      3
   4 │     4      2      1
```
