```
VectorContinousComponentCallback(condition, affect, len; kwargs...)
```

[`ComponentCondition`](@ref) と [`ComponentAffect`](@ref) を接続し、[`add_callback!`](@ref) または [`set_callback!`](@ref) を使用してコンポーネントモデルに添付できる連続コールバックを作成します。このベクトルバージョンは、`len` 出力次元を持つ `condions` を許可します。`affect` は、ゼロクロッシングが検出された次元を知るために追加の `event_idx` 引数でトリガーされます。

`kwargs` は、コンポーネントベースのコールバックがネットワーク全体のために収集される際に `VectorContinuousCallback` に転送されます。利用可能なオプションについては、[`DiffEq.jl docs`](https://docs.sciml.ai/DiffEqDocs/stable/features/callback_functions/) を参照してください。
