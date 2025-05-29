```
scanmle(data; ntrials=100, stderrcutoff=0.1, useKS=false)
```

Perform `mle` approximately `ntrials` times on `data`, increasing `xmin`. Stop trials if the standard error of the estimate `alpha` is greater than `stderrcutoff`. If `useKS` is true, then the application of `mle` giving the smallest KS statistic is returned. Return an object containing statistics of the scan.

`scanmle` is intended to analayze the power-law behavior of the tail of data.
