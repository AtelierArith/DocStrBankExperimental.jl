```
openblas_pinthreads(cpuids; nthreads = BLAS.get_num_threads())
```

指定されたCPU IDにOpenBLASスレッドをピン留めします。オプションのキーワード引数`nthreads`はカットオフとして機能します。
