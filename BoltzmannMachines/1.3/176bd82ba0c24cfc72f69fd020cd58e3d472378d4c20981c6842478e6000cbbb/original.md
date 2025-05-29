```
monitorloglikelihood!(monitor, rbm, epoch, datadict)
```

Estimates the log-likelihood of the `datadict`'s data sets in the RBM model `rbm` with AIS and stores the values, together with information about the variance of the estimator, in the `monitor`.

If there is more than one worker available, the computation is parallelized by default. Parallelization can be turned on or off with the optional boolean argument `parallelized`.

For the other optional keyword arguments, see `aislogimportanceweights`.

See also: `loglikelihood`.
