```
worker_start_command(
    runmode::DynamicAddProcsMode,
    manager::ClusterManager = ParallelProcessingTools.ppt_cluster_manager()
)::Tuple{Cmd,Integer,Integer}
```

タプル `(cmd, m, n)` を返します。ここで、システムコマンド `cmd` は `n` 人のワーカーを開始するために `m` 回（並行して）実行する必要があります。
