```
unpinthread(; threadid::Integer = Threads.threadid())
```

指定されたJuliaスレッドのピンを外し、アフィニティマスクをすべてのユニティに設定します。その後、OSはJuliaスレッドをあるCPUスレッドから別のCPUスレッドに移動することができます。
