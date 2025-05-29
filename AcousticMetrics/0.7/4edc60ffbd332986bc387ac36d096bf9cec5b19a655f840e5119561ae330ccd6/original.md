```
ExactProportionalBands{NO,LCU}(TF=Float64, bstart::Int, bend::Int, scaler=1)
```

Construct an `ExactProportionalBands` with `eltype` `TF` encomposing band index numbers from `bstart` to `bend`.

The "standard" band frequencies will be scaled by `scaler`, e.g. if `scaler = 0.5` then what would normally be the `1000 Hz` frequency will be `500 Hz`, etc..
