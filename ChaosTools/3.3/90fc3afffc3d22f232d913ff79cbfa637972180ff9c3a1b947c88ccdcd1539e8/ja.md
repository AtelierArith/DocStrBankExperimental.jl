```
lyapunov(pds::ParallelDynamicalSystem, T; Ttr, Δt, d0, d0_upper, d0_lower)
```

`lyapunov(ds::DynamicalSystem, ...)`によって呼び出される低レベルのメソッドです。このメソッドを使用して、異なる初期条件やパラメータをループ処理するには、`pds`に対して[`reinit!`](@ref)を呼び出します。
