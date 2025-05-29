```
convert_arguments(P, Matrix)::Tuple{ClosedInterval, ClosedInterval, Matrix}
```

Takes an `AbstractMatrix`, converts the dimesions `n` and `m` into `ClosedInterval`, and stores the `ClosedInterval` to `n` and `m`, plus the original matrix in a Tuple.

`P` is the plot Type (it is optional).
