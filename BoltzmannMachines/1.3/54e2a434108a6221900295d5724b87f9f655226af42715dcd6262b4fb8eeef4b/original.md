```
monitorlogproblowerbound!(monitor, dbm, epoch, datadict)
```

Estimates the lower bound of the log probability of the `datadict`'s data sets in the DBM `dbm` with AIS and stores the values, together with information about the variance of the estimator, in the `monitor`.

If there is more than one worker available, the computation is parallelized by default. Parallelization can be turned on or off with the optional boolean argument `parallelized`.

For the other optional keyword arguments, see `aislogimpweights`.

See also: `logproblowerbound`.
