```
Sim(m::MDP, p::Policy[, initialstate]; kwargs...)
Sim(m::POMDP, p::Policy[, updater[, initial_belief[, initialstate]]]; kwargs...)
```

シミュレーションを実行し記録するために必要なすべてを含む `Sim` オブジェクトを作成します。これにはモデル、初期条件、およびメタデータが含まれます。

`Sim` オブジェクトのベクトルは、[`run`](@ref) または [`run_parallel`](@ref) を使用して実行できます。

## キーワード引数

  * `rng::AbstractRNG=Random.default_rng()`
  * `max_steps::Int=typemax(Int)`
  * `simulator::Simulator=HistoryRecorder(rng=rng, max_steps=max_steps)`
  * `metadata::NamedTuple シミュレーションのためのメタデータの名前付きタプル（または辞書）で、記録されます。例：`(solver_iterations=500,)`。
