```
variable_pump_switch_off(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

ネットワーク内のポンプに対してバイナリ変数を作成します。サブネットワーク（または時間）インデックス `nw` において、すなわち `pump` の `a` に対して `z_switch_off_pump[a]` が作成されます。ここで、1はポンプが現在のサブネットワーク（または時間）インデックスで「オフ」状態に切り替えられたことを示し、0はポンプに状態の変化がなかったことを示します。
