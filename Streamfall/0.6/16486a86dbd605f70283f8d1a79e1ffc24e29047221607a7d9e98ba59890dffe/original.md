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

Use a single objective function to calibrate a network or a single node in a network.
