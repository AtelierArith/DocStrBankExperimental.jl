```
worker_start_command(
    runmode::DynamicAddProcsMode,
    manager::ClusterManager = ParallelProcessingTools.ppt_cluster_manager()
)::Tuple{Cmd,Integer,Integer}
```

Return a tuple `(cmd, m, n)`, with system command `cmd` that needs to be run `m` times (in parallel) to start `n` workers.
