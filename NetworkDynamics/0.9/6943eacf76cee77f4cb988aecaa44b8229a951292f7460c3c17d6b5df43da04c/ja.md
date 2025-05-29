```
ContinousComponentCallback(condition, affect; kwargs...)
```

[`ComponentCondition`](@ref) と [`ComponentAffect`](@ref) を接続し、[`add_callback!`](@ref) または [`set_callback!`](@ref) を使用してコンポーネントモデルに添付できる連続コールバックを作成します。

`kwargs` は、コンポーネントベースのコールバックがネットワーク全体のために収集される際に `VectorContinuousCallback` に転送されます。利用可能なオプションについては [`DiffEq.jl docs`](https://docs.sciml.ai/DiffEqDocs/stable/features/callback_functions/) を参照してください。
