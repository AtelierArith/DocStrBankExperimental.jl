```julia
fold!(
    design::ExperimentalDesign.FractionalFactorial2Level
) -> DataFrames.DataFrame

```

```jldoctest
julia> fold!(FractionalFactorial2Level(@formula(y ~ a + b + a&b + c + a&c+ b&c + a&b&c)))
16×7 DataFrame
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
   9 │     1      1      1     -1     -1     -1      1
  10 │    -1      1      1      1      1     -1     -1
  11 │     1     -1      1      1     -1      1     -1
  12 │    -1     -1      1     -1      1      1      1
  13 │     1      1     -1     -1      1      1     -1
  14 │    -1      1     -1      1     -1      1      1
  15 │     1     -1     -1      1      1     -1      1
  16 │    -1     -1     -1     -1     -1     -1     -1

```
