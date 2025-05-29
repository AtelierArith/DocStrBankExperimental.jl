```
maxdim!(sw::Sweeps,maxdims::Int...)
```

Set the maximum MPS bond dimension for each sweep by providing up to `nsweep(sw)` values. If fewer values are provided, the last value is repeated for the remaining sweeps.
