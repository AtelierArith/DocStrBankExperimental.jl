```julia
FullFactorial(
    factors::Array
) -> ExperimentalDesign.FullFactorial

```

```jldoctest
julia> FullFactorial(fill([-1, 1], 3))
FullFactorial
Dimension: (8, 3)
Factors: (factor1 = [-1, 1], factor2 = [-1, 1], factor3 = [-1, 1])
Formula: 0 ~ factor1 + factor2 + factor3
Design Matrix:
8×3 DataFrame
 Row │ factor1  factor2  factor3
     │ Int64    Int64    Int64
─────┼───────────────────────────
   1 │      -1       -1       -1
   2 │       1       -1       -1
   3 │      -1        1       -1
   4 │       1        1       -1
   5 │      -1       -1        1
   6 │       1       -1        1
   7 │      -1        1        1
   8 │       1        1        1

```
