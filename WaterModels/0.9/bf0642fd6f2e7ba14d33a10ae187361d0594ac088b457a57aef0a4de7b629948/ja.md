```
variable_pump_switch_on(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

ネットワーク内のポンプに対するバイナリ変数をサブネットワーク（または時間）インデックス `nw` で作成します。すなわち、`z_switch_on_pump[a]` は `pump` の `a` に対して、1 はポンプが現在のサブネットワーク（または時間）インデックスで「オン」状態に切り替えられたことを示し、0 はポンプに状態の変化がなかったことを示します。
