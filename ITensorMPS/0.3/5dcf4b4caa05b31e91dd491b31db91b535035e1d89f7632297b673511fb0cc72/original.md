```
cutoff!(sw::Sweeps,maxdims::Int...)
```

Set the MPS truncation error used for each sweep by providing up to `nsweep(sw)` values. If fewer values are provided, the last value is repeated for the remaining sweeps.
