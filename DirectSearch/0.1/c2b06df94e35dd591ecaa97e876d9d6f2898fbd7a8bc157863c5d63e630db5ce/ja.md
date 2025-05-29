```
CacheLoadJLD2(p::AbstractProblem{T}, path::String, dataset::String="cache_costs") where T
```

提供されたJLD2ファイルとデータセットからコストをキャッシュにロードします。`path`は相対パスまたは絶対パスであり、'.jld2'拡張子を含む必要があります。デフォルトでは、'cache_costs'という名前のデータセットからロードされます。
