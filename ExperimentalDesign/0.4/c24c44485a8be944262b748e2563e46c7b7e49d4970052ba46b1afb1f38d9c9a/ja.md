```julia
CentralComposite(
    formula::StatsModels.FormulaTerm;
    center,
    alpha,
    face
) -> ExperimentalDesign.CentralComposite

```

```jldoctest
julia> CentralComposite(@formula(y ~ -1 + factor1 & factor1 + factor2 & factor2 + factor3 & factor3 + factor1 & factor2 + factor1 & factor3 + factor2 & factor3 + factor1 + factor2 + factor3))
CentralComposite
Dimension: (22, 3)
Factors: (:factor1, :factor2, :factor3)
Formula: y ~ -1 + factor1 + factor2 + factor3 + factor1 & factor1 + factor2 & factor2 + factor3 & factor3 + factor1 & factor2 + factor1 & factor3 + factor2 & factor3
Alpha: orthogonal
Face: circumscribed
Design Matrix:
22×3 DataFrame
 Row │ factor1   factor2   factor3
     │ Float64   Float64   Float64
─────┼──────────────────────────────
   1 │ -1.0      -1.0      -1.0
   2 │  1.0      -1.0      -1.0
   3 │ -1.0       1.0      -1.0
   4 │  1.0       1.0      -1.0
   5 │ -1.0      -1.0       1.0
   6 │  1.0      -1.0       1.0
   7 │ -1.0       1.0       1.0
   8 │  1.0       1.0       1.0
  ⋮  │    ⋮         ⋮         ⋮
  16 │  0.0       1.82574   0.0
  17 │  0.0       0.0      -1.82574
  18 │  0.0       0.0       1.82574
  19 │  0.0       0.0       0.0
  20 │  0.0       0.0       0.0
  21 │  0.0       0.0       0.0
  22 │  0.0       0.0       0.0
                      7 rows omitted

```
