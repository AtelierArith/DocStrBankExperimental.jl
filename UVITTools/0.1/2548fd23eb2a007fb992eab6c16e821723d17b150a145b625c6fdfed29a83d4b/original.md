```
uvit_saturation_corr(count_rate[, frames_per_sec=28.717])
```

Correct UVIT source count rate for saturation effect.

This function is based on the algorithm provided in Tandon et al. (2017),  and used by `uvit_aphot.jl` for circular extraction region only.
