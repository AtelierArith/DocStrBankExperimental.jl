```
scaling_benchmark(; threads=1:Threads.nthreads(), kwargs...)
```

スレッド数（`threads`で示される）に応じた包括的なSTREAMベンチマークを実行します。各スレッド数に対する測定された最大メモリ帯域幅（MB/s）のベクトルを返します。
