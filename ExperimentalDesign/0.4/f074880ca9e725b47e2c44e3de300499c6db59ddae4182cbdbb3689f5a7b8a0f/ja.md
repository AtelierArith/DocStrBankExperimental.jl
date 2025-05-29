```julia
FullFactorial(
    factors::NamedTuple,
    formula::StatsModels.FormulaTerm
) -> ExperimentalDesign.FullFactorial

```

```jldoctest
julia> FullFactorial((A = [1, 2, 4], B = [:a, :b], C = [1.0, -1.0]), @formula(y ~ A + B +C))
FullFactorial
Dimension: (12, 3)
Factors: (A = [1, 2, 4], B = [:a, :b], C = [1.0, -1.0])
Formula: y ~ A + B + C
Design Matrix:
12×3 DataFrame
 Row │ A    B    C
     │ Any  Any  Any
─────┼────────────────
   1 │ 1    a    1.0
   2 │ 2    a    1.0
   3 │ 4    a    1.0
   4 │ 1    b    1.0
   5 │ 2    b    1.0
   6 │ 4    b    1.0
   7 │ 1    a    -1.0
   8 │ 2    a    -1.0
   9 │ 4    a    -1.0
  10 │ 1    b    -1.0
  11 │ 2    b    -1.0
  12 │ 4    b    -1.0

```
