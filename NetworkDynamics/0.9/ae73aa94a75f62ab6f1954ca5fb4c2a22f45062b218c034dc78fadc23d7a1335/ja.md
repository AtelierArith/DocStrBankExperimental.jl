```
DiscreteComponentCallback(condition, affect; kwargs...)
```

[`ComponentCondition`](@ref) と [`ComponentAffect`](@ref) を接続し、コンポーネントモデルに [`add_callback!`](@ref) または [`set_callback!`](@ref) を使用して添付できる離散コールバックを作成します。

`condition` 関数はブール値を返すことに注意してください。離散コールバックはルート探索を行わないためです。

`kwargs` は、コンポーネントベースのコールバックがネットワーク全体のために収集される際に `DiscreteCallback` に転送されます。利用可能なオプションについては [`DiffEq.jl docs`](https://docs.sciml.ai/DiffEqDocs/stable/features/callback_functions/) を参照してください。
