```julia
PlackettBurman(
    formula::StatsModels.FormulaTerm;
    symbol_encoding
) -> ExperimentalDesign.PlackettBurman

```

```jldoctest
julia> PlackettBurman(@formula(y ~ x1 + x2 + x3 + x4))
PlackettBurman
Dimension: (8, 7)
Factors: (:x1, :x2, :x3, :x4)
Dummy Factors: (:dummy1, :dummy2, :dummy3)
Formula: y ~ -1 + x1 + x2 + x3 + x4 + dummy1 + dummy2 + dummy3
Design Matrix:
8×7 DataFrame
 Row │ x1     x2     x3     x4     dummy1  dummy2  dummy3
     │ Int64  Int64  Int64  Int64  Int64   Int64   Int64
─────┼────────────────────────────────────────────────────
   1 │     1      1      1      1       1       1       1
   2 │    -1      1     -1      1       1      -1      -1
   3 │     1     -1      1      1      -1      -1      -1
   4 │    -1      1      1     -1      -1      -1       1
   5 │     1      1     -1     -1      -1       1      -1
   6 │     1     -1     -1     -1       1      -1       1
   7 │    -1     -1     -1      1      -1       1       1
   8 │    -1     -1      1     -1       1       1      -1

```
