```
log_histogram(logger, name, (bins,weights); step=step(logger))
```

Logs a histogram under the tag `name` on given `step`. The histogram must be passed as a tuple holding the `N+1` bin edges and the height of the `N` bins.

You can also pass the raw data, and a binning algorithm from `StatsBase.jl` will be used to bin the data.
