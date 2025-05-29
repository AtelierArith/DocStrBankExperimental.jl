```
process_cov(filename, folder) -> Vector{CovCount}
```

与えられたJuliaソースファイルのファイル名に基づいて、すべての一致する.{pid}.covファイルを読み込むことによって、行のカバレッジカウントの配列を生成します。
