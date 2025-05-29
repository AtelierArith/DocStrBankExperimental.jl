```
remd_exchange!(sys, sim, n, m; n_threads=Threads.nthreads(), rng=Random.default_rng())
```

REMDシミュレーション中に[`ReplicaSystem`](@ref)でレプリカ`n`と`m`の交換を試みます。

成功した交換は、適切に座標と速度を交換します。受け入れ量`Δ`と、交換が成功したかどうかを示す`Bool`を返します。
