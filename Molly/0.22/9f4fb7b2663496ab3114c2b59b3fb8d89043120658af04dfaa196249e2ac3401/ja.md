```
total_energy(system, neighbors=find_neighbors(sys); n_threads=Threads.nthreads())
```

システムの総エネルギーを、[`kinetic_energy`](@ref) と [`potential_energy`](@ref) の合計として計算します。
