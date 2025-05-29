```
variable_pump_indicator(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

ネットワーク内のサブネットワーク（または時間）インデックス `nw` に対してポンプのバイナリ変数を作成します。すなわち、`z_pump[a]` は `pump` における `a` に対して、1 はポンプが現在稼働していること（すなわち、オン）を示し、0 はポンプが稼働していないこと（すなわち、オフ）を示します。
