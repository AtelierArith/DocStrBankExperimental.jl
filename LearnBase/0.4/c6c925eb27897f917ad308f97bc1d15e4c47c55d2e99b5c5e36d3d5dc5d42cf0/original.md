```
 datasubset(data, [idx], [obsdim])
```

Return a lazy subset of the observations in `data` that correspond to the given `idx`. No data should be copied except of the indices. Note that `idx` can be of type `Int` or `AbstractVector`. Both options must be supported by a custom type.

If it makes sense for the type of `data`, `obsdim` can be used to disptach on which dimension of `data` denotes the observations. See `?ObsDim`.
