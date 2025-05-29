```
optimize_gridsize(nx0,ny0[;region_size=4,optimize_threads=true,nthreads_max=length(cpu_info()),nsamp=1])
```

名目上のグリッドサイズ（`nx0` x `ny0`）に基づいて、計算時間を最小化する最適なグリッドサイズを決定します。オプションの引数には、`optimize_threads` フラグと最大スレッド数 `nthreads_max`（マルチスレッドが許可されている場合）および各試行の CPU 時間のサンプル数が含まれます。最適な `nx`、`ny`、および対応する CPU 時間を返します。
