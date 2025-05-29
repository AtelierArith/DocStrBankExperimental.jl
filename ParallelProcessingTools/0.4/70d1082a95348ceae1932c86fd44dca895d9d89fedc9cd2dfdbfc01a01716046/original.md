```
write_worker_start_script(
    filename::AbstractString,
    runmode::DynamicAddProcsMode,
    manager::ClusterManager = ParallelProcessingTools.ppt_cluster_manager()
)
```

Writes the system command to start worker processes to a shell script.
