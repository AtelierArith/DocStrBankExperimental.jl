```
function push_info!(logger, [level,] v; continues::Bool=false)
```

文字列 `v` をロガーにプッシュします。もし continues=true の場合、次の `push_info!` (または `push_iteration_info!`) はこれに接続されます。例えば、改行は省略されます。
