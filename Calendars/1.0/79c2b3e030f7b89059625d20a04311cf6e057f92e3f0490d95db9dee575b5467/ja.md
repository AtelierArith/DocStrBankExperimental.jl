```julia
PrintIsoWeek(year::DPart, week::DPart, io=stdout)
```

指定されたIso週のカレンダーを`io`にマークダウンテーブルとして印刷します。

例えば：

```julia
julia> PrintIsoWeek(2022, 2)
```
