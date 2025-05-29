```
variable_block_indicator(
    pm::AbstractUnbalancedPowerModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

負荷ブロックごとのブロックステータスのための変数を作成します。$z^{bl}_i\in{0,1}~\forall i \in B$、`relax=false`の場合はバイナリです。変数は`report=true`の場合に解に現れます。
