```
ParallelTemperingMC <: AbstractMC
```

`AbstractMC` インターフェースの [parallel run mode](@ref parallel_run_mode) の実装で、他の `AbstractMC` 実装を並列テンパリングで実行します。

子クラスの実装は以下を実装することが期待されます。

  * [`parallel_tempering_log_weight_ratio`](@ref)
  * [`parallel_tempering_change_parameter!`](@ref)
