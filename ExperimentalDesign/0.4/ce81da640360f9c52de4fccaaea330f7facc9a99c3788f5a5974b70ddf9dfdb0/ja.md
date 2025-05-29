```julia
FractionalFactorial2Level(
    formula::StatsModels.FormulaTerm
) -> ExperimentalDesign.FractionalFactorial2Level

```

```jldoctest
julia> FractionalFactorial2Level(@formula(y ~ a + b + a&b + c + a&c+ b&c + a&b&c))
FractionalFactorial2Level
Dimension: (8, 7)
Factors: (a = [-1, 1], b = [-1, 1], c = [-1, 1])
Formula: y ~ a + b + c + a & b + a & c + b & c + a & b & c
Design Matrix:
8×7 DataFrame
 Row │ a      b      c      a_b    a_c    b_c    a_b_c
     │ Int64  Int64  Int64  Int64  Int64  Int64  Int64
─────┼─────────────────────────────────────────────────
   1 │    -1     -1     -1      1      1      1     -1
   2 │     1     -1     -1     -1     -1      1      1
   3 │    -1      1     -1     -1      1     -1      1
   4 │     1      1     -1      1     -1     -1     -1
   5 │    -1     -1      1      1     -1     -1      1
   6 │     1     -1      1     -1      1     -1     -1
   7 │    -1      1      1     -1     -1      1     -1
   8 │     1      1      1      1      1      1      1

```
