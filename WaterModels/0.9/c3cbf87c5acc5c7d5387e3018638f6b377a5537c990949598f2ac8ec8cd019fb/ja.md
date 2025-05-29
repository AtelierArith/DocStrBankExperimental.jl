```
variable_regulator_indicator(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

ネットワーク内のサブネットワーク（または時間）インデックス `nw` に対して、レギュレーターのバイナリ変数を作成します。すなわち、`z_regulator[a]` は `regulator` における `a` に対して、圧力低下レギュレーターが現在アクティブであることを示す1、そうでない場合は0を示します。
