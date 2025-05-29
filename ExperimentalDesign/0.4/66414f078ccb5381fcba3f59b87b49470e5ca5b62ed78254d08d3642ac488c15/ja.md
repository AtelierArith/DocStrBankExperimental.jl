```julia
BoxBehnken(
    factors::Int64;
    center
) -> ExperimentalDesign.BoxBehnken

```

```jldoctest
julia> BoxBehnken(3, center=3)
BoxBehnken
Dimension: (15, 3)
Factors: (:factor1, :factor2, :factor3)
Formula: y ~ -1 + factor1 & factor1 + factor2 & factor2 + factor3 & factor3 + factor1 & factor2 + factor1 & factor3 + factor2 & factor3 + factor1 + factor2 + factor3
Design Matrix:
15×3 DataFrame
 Row │ factor1  factor2  factor3
     │ Float64  Float64  Float64
─────┼───────────────────────────
   1 │    -1.0     -1.0      0.0
   2 │     1.0     -1.0      0.0
   3 │    -1.0      1.0      0.0
   4 │     1.0      1.0      0.0
   5 │    -1.0      0.0     -1.0
   6 │     1.0      0.0     -1.0
   7 │    -1.0      0.0      1.0
   8 │     1.0      0.0      1.0
   9 │     0.0     -1.0     -1.0
  10 │     0.0      1.0     -1.0
  11 │     0.0     -1.0      1.0
  12 │     0.0      1.0      1.0
  13 │     0.0      0.0      0.0
  14 │     0.0      0.0      0.0
  15 │     0.0      0.0      0.0

```
