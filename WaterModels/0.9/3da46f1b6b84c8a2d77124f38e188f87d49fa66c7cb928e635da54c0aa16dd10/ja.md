```
variable_valve_indicator(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

ネットワーク内のバルブに対するバイナリ変数をサブネットワーク（または時間）インデックス `nw` で作成します。すなわち、`valve` の `a` に対して `z_valve[a]` を作成します。ここで、1はバルブが開いていることを示し、0はバルブが閉じていることを示します。
