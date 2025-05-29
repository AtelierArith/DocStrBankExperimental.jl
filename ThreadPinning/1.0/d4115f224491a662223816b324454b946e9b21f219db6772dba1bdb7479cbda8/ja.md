```
getaffinity(; threadid = Threads.threadid(), cutoff = cpuidlimit())
```

Juliaスレッドのスレッドアフィニティを取得します。アフィニティマスクをゼロと一のベクトルとして返します。デフォルトでは、マスクは`Sys.CPU_THREADS`でカットオフされます。これは、`cutoff`キーワード引数を介して調整できます（`nothing`はカットオフなしを意味します）。
