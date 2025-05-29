```
CommonLogDensity(nparameters, sample_init, lπ)
```

this function will return a type for performing classical MCMC via the `sample` function.

`nparameters`: total number of parameters per sample.

`sample_init`: function which accepts an `RNG::AbstractRNG` and returns a sample for `lπ`.

`lπ`: function which accepts a sample, and returns a log-density float value.
