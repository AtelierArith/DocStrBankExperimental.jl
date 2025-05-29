# テイル

```julia
tail(ts::TSFrame, n::Int = 10)
```

`ts`の最後の`n`行を返します。

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random)
julia> tail(TSFrame(1:100))
(10 x 1) TSFrame with Int64 Index

 Index  x1
 Int64  Int64
──────────────
    91     91
    92     92
    93     93
    94     94
    95     95
    96     96
    97     97
    98     98
    99     99
   100    100
```
