```
logpartitionfunction(bm; ...)
logpartitionfunction(bm, logr)
```

Calculates or estimates the log of the partition function of the Boltzmann Machine `bm`.

`r` is an estimator of the ratio of the `bm`'s partition function Z to the partition function Z*0 of the reference BM with zero weights but same biases as the given `bm`. In case of a GaussianBernoulliRBM, the reference model also has the same standard deviation parameter. The estimated partition function of the Boltzmann Machine is Z = r * Z*0 with `r` being the mean of the importance weights. Therefore, the log of the estimated partition function is log(Z) = log(r) + log(Z_0)

If the log of `r` is not given as argument `logr`, Annealed Importance Sampling (AIS) is performed to get a value for it. In this case, the optional arguments for AIS can be specified (see `aislogimpweights`), and the optional boolean argument `parallelized` can be used to turn on batch-parallelized computing of the importance weights.
