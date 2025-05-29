```
convert_arguments(P, Matrix)::Tuple{ClosedInterval, ClosedInterval, ClosedInterval, Matrix}
```

Takes an array of `{T, 3} where T`, converts the dimesions `n`, `m` and `k` into `ClosedInterval`, and stores the `ClosedInterval` to `n`, `m` and `k`, plus the original array in a Tuple.

`P` is the plot Type (it is optional).
