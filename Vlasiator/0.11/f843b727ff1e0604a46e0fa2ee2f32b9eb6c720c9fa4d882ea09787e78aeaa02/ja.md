```
extractsat(files::AbstractVector{String}, var::String, cid::Int)
```

固定セルID `cid` から `files` での `var` のマルチスレッド抽出。これは、`files` が同じグリッド構造から来ていると仮定します。
