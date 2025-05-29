```
calibrate!(
    sn::StreamfallNetwork, climate::Climate, calib_data::DataFrame, metric::C;
    kwargs...
) where {F,C}
calibrate!(
    sn::StreamfallNetwork, v_id::Int64, climate::Climate, calib_data::DataFrame, metric::C;
    kwargs...
) where {F,C}
```

ネットワークまたはネットワーク内の単一ノードをキャリブレーションするために、単一の目的関数を使用します。
