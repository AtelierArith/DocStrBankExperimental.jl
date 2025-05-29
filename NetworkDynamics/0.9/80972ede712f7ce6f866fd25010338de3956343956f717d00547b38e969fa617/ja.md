```
PresetTimeComponentCallback(ts, affect; kwargs...)
```

指定されたタイムステップ `ts` で [`ComponentAffect`](@ref) をトリガーする離散コールバックで、これは [`add_callback!`](@ref) または [`set_callback!`](@ref) を使用してコンポーネントモデルに添付できます。

`kwargs` は、コンポーネントベースのコールバックがネットワーク全体のために収集されるときに、[`PresetTimeCallback`](@extref DiffEqCallbacks.PresetTimeCallback) に転送されます。 

`PresetTimeCallback` は、ソルバーにタイムステップを追加し、正確なタイミングでトリガーされることを保証します。
