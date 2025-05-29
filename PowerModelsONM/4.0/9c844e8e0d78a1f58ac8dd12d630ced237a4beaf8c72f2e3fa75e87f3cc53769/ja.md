```
variable_switch_state(
    pm::AbstractUnbalancedPowerModel;
    nw::Int=nw_id_default,
    report::Bool=true,
    relax::Bool=false
)
```

スイッチ状態（開/閉）変数のための変数を作成します。$\gamma_i\in{0,1}~\forall i \in S$、`relax=false`の場合はバイナリです。非 dispatchable スイッチの変数は `VariableRef` ではなく定数になります。変数は `report=true` の場合に解に現れます。
