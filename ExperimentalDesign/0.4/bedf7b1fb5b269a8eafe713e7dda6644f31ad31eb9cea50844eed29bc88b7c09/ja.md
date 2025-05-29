```julia
FullFactorial(
    factors::Tuple
) -> ExperimentalDesign.FullFactorial

```

```jldoctest
julia> FullFactorial(([1, 2, 4], [:a, :b], [1.0, -1.0]))
FullFactorial
Dimension: (12, 3)
Factors: (factor1 = [1, 2, 4], factor2 = [:a, :b], factor3 = [1.0, -1.0])
Formula: 0 ~ factor1 + factor2 + factor3
Design Matrix:
12×3 DataFrame
 Row │ factor1  factor2  factor3
     │ Any      Any      Any
─────┼───────────────────────────
   1 │ 1        a        1.0
   2 │ 2        a        1.0
   3 │ 4        a        1.0
   4 │ 1        b        1.0
   5 │ 2        b        1.0
   6 │ 4        b        1.0
   7 │ 1        a        -1.0
   8 │ 2        a        -1.0
   9 │ 4        a        -1.0
  10 │ 1        b        -1.0
  11 │ 2        b        -1.0
  12 │ 4        b        -1.0

```
