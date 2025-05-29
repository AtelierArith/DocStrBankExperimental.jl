```julia
OptimLHCDesign(
    n::Int64,
    d::Int64,
    gens
) -> ExperimentalDesign.OptimLHCDesign

```

```jldoctest
julia> OptimLHCDesign(5,3,4)
OptimLHCDesign
Dimension: (5, 3)
Factors: (:factor1, :factor2, :factor3)
Fitness: [1.3760238272524201, 1.3760238272524201, 1.3760238272524201, 1.3760238272524201, 1.3760238272524201]
Design Matrix:
5×3 DataFrame
 Row │ factor1  factor2  factor3
     │ Int64    Int64    Int64
─────┼───────────────────────────
   1 │       3        5        2
   2 │       5        1        3
   3 │       4        4        5
   4 │       2        2        1
   5 │       1        3        4
```
