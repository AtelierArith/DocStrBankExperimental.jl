```
stopworkers()
stopworkers(pid::Int)
stopworkers(pids::AbstractVector{Int})
```

すべてのワーカー プロセスまたは指定されたワーカー プロセスを停止します。現在のプロセスは無視されます。
