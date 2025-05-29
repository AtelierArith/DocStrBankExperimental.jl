```
simulate_remd!(sys, remd_sim, n_steps; n_threads=Threads.nthreads(),
               run_loggers=true, rng=Random.default_rng())
```

[`ReplicaSystem`](@ref)を使用して、REMDシミュレーションを実行します。

現在、ステップ数に依存する相互作用とは互換性がありません。
