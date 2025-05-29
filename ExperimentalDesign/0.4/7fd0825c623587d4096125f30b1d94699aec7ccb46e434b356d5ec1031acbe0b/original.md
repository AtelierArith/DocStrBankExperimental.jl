```julia
RandomLHCDesign(
    n::Int64,
    d::Int64
) -> ExperimentalDesign.RandomLHCDesign

```

```jldoctest
julia> RandomLHCDesign(4,3)
RandomLHCDesign
Dimension: (4, 3)
Factors: (:factor1, :factor2, :factor3)
Design Matrix:
4×3 DataFrame
 Row │ factor1  factor2  factor3
     │ Int64    Int64    Int64
─────┼───────────────────────────
   1 │       1        4        4
   2 │       2        1        2
   3 │       3        3        3
   4 │       4        2        1

```
