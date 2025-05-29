```
calibrate!(
    sn::StreamfallNetwork,
    climate::Climate,
    calib_data::DataFrame,
    metric::AbstractDict{String,F};
    kwargs...
)
```

ストリームネットワークをキャリブレーションします。
