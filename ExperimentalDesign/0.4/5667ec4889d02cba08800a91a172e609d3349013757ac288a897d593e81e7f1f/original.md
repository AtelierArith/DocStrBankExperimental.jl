```julia
OptimLHCDesign(
    n::Int64,
    factors::Tuple,
    gens
) -> ExperimentalDesign.OptimLHCDesign

```

```jldoctest
julia> OptimLHCDesign(5,Tuple((:A,:B,:C)),4)
OptimLHCDesign
Dimension: (5, 3)
Factors: (:A, :B, :C)
Fitness: [1.3760238272524201, 1.3760238272524201, 1.3760238272524201, 1.3760238272524201, 1.3760238272524201]
Design Matrix:
5×3 DataFrame
 Row │ A      B      C
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     3      5      2
   2 │     5      1      3
   3 │     4      4      5
   4 │     2      2      1
   5 │     1      3      4

```
