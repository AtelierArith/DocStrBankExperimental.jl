```
ApproximateOctaveBands{LCU,TF}(bstart::Int, bend::Int)
```

Construct an `ApproximateOctaveBands` with `eltype` `TF` encomposing band index numbers from `bstart` to `bend`.

The "standard" band frequencies will be scaled by `scaler`, e.g. if `scaler = 0.5` then what would normally be the `1000 Hz` frequency will be `500 Hz`, etc..
