```
Impute.locf(data; dims=1)
```

Iterates forwards through the `data` and fills missing data with the last existing observation. See [`Impute.LOCF`](@ref) for details.

# Example

```jldoctest
julia> using DataFrames; using Impute: Impute


julia> df = DataFrame(:a => [1.0, 2.0, missing, missing, 5.0], :b => [1.1, 2.2, 3.3, missing, 5.5])
5×2 DataFrame
 Row │ a          b
     │ Float64?   Float64?
─────┼──────────────────────
   1 │       1.0        1.1
   2 │       2.0        2.2
   3 │ missing          3.3
   4 │ missing    missing
   5 │       5.0        5.5

julia> Impute.locf(df)
5×2 DataFrame
 Row │ a         b
     │ Float64?  Float64?
─────┼────────────────────
   1 │      1.0       1.1
   2 │      2.0       2.2
   3 │      2.0       3.3
   4 │      2.0       3.3
   5 │      5.0       5.5
```
