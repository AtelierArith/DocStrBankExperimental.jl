```
Impute.nocb(data; dims=1)
```

`data`を逆方向に反復処理し、次の既存の観測値で欠損データを埋めます。詳細については[`Impute.NOCB`](@ref)を参照してください。

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

julia> Impute.nocb(df)
5×2 DataFrame
 Row │ a         b
     │ Float64?  Float64?
─────┼────────────────────
   1 │      1.0       1.1
   2 │      2.0       2.2
   3 │      5.0       3.3
   4 │      5.0       5.5
   5 │      5.0       5.5
```
