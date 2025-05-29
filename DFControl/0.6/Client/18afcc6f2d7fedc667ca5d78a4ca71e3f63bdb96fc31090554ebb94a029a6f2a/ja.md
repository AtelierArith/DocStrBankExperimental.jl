```
outputdata(job::Job; server = job.server, calcs::Vector{String}=String[])
```

[`Job`](@ref) の各計算の出力ファイルを見つけ、すべての解析データを辞書にグループ化します。
