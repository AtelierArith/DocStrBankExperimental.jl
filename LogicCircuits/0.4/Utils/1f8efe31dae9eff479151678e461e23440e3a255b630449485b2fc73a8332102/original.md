```
make_missing_mcar(d::DataFrame; keep_prob::Float64=0.8)
```

Returns a copy of dataframe with making some features missing as MCAR, with `keep_prob` as probability of keeping each feature.
