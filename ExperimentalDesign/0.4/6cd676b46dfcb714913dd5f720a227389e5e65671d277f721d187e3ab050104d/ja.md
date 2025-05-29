```julia
PlackettBurman(
    factors::Int64
) -> ExperimentalDesign.PlackettBurman

```

```jldoctest
julia> PlackettBurman(4)
PlackettBurman
Dimension: (8, 7)
Factors: (:factor1, :factor2, :factor3, :factor4)
Dummy Factors: (:dummy1, :dummy2, :dummy3)
Formula: 0 ~ -1 + factor1 + factor2 + factor3 + factor4 + dummy1 + dummy2 + dummy3
Design Matrix:
8×7 DataFrame
 Row │ factor1  factor2  factor3  factor4  dummy1  dummy2  dummy3
     │ Int64    Int64    Int64    Int64    Int64   Int64   Int64
─────┼────────────────────────────────────────────────────────────
   1 │       1        1        1        1       1       1       1
   2 │      -1        1       -1        1       1      -1      -1
   3 │       1       -1        1        1      -1      -1      -1
   4 │      -1        1        1       -1      -1      -1       1
   5 │       1        1       -1       -1      -1       1      -1
   6 │       1       -1       -1       -1       1      -1       1
   7 │      -1       -1       -1        1      -1       1       1
   8 │      -1       -1        1       -1       1       1      -1

```
