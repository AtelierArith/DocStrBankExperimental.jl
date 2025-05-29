```
extract_peak_interval(run; α, n)
```

Takes a CoulterCounterRun `run` and fits a kernel density estimate to smooth out binning effects by the machine and then finds the largest peak. It returns the diameter corresponding to the location of this peak as well as the max and min diameters of the confidence interval defined by `α`. This interval is generated on the empirically by bootstrapping the data `n` times.
