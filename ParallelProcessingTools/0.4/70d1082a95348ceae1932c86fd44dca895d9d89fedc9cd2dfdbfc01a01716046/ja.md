```
write_worker_start_script(
    filename::AbstractString,
    runmode::DynamicAddProcsMode,
    manager::ClusterManager = ParallelProcessingTools.ppt_cluster_manager()
)
```

ワーカープロセスを開始するためのシステムコマンドをシェルスクリプトに書き込みます。
