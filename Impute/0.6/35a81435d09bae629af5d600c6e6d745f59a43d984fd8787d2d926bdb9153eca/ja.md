```
Impute.interp(data; dims=1)
```

ベクトル内の最も近い値の間で線形補間を行います。詳細については [`Impute.Interpolate`](@ref) を参照してください。

# 例

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

julia> Impute.interp(df)
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
