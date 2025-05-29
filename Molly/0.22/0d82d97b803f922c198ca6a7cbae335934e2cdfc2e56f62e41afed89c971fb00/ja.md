```
accelerations(system, neighbors=find_neighbors(sys), step_n=0; n_threads=Threads.nthreads())
```

システム内のすべての原子の加速度を、ペアワイズ、特定および一般的な相互作用とニュートンの運動の第二法則を使用して計算します。
