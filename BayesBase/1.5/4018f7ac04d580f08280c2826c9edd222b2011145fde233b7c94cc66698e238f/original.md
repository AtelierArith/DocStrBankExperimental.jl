```
logpdf_sampling_optimized(d)
```

`logpdf_sample_optimized` function takes as an input a distribution `d` and returns corresponding optimized two versions  for taking `logpdf()` and sampling with `rand!` respectively. Alias for `(logpdf_optimized(d), sampling_optimized(d))`, but can be specialized.
