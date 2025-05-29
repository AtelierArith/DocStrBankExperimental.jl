```julia
PrintEuropeanMonth(year::DPart, month::DPart, io=stdout)
```

指定されたヨーロッパの月のカレンダーを`io`にマークダウンテーブルとして印刷します。

例えば：

```julia
julia> PrintEuropeanMonth(2022, 2)
```
