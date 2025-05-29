```
impute!(table, imp; cols=nothing) -> table
```

Imputes the data in a table by imputing the values 1 column at a time; if this is not the desired behaviour custom imputor methods should overload this method.

# Arguments

  * `imp::Imputor`: the Imputor method to use
  * `table`: the data to impute

# Keyword Arguments

  * `cols`: The columns to impute along (default is to impute all columns)

# Returns

  * the input `data` with values imputed

# Example

```jldoctest
julia> using DataFrames; using Impute: Interpolate, impute


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

julia> impute(df, Interpolate())
5×2 DataFrame
 Row │ a         b
     │ Float64?  Float64?
─────┼────────────────────
   1 │      1.0       1.1
   2 │      2.0       2.2
   3 │      3.0       3.3
   4 │      4.0       4.4
   5 │      5.0       5.5
```
