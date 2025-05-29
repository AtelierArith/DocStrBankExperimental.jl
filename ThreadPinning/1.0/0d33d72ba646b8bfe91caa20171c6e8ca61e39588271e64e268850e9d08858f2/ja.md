```
openblas_unpinthreads(; threadpool = :default)
```

すべてのOpenBLASスレッドのアフィニティマスクをユニティに設定することで、すべてのOpenBLASスレッドのピン留めを解除します。その後、OSは任意のOpenBLASスレッドを1つのCPUスレッドから別のCPUスレッドに移動することができます。
