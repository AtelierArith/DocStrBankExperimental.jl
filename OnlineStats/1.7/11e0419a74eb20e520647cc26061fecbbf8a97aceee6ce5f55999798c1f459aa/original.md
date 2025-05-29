```
Trace(stat, b=500, f=value)
```

Wrapper around an OnlineStat that stores `b` "snapshots" (a fixed copy of the OnlineStat).  The snapshots are taken at approximately equally-spaced intervals between 0 and the current `nobs`.  The main use case is visualizing state changes as observations are added.

# Example

```
using OnlineStats, Plots

o = Trace(Mean(), 10)

fit!(o, 1:100)

OnlineStats.snapshots(o)

plot(o)
```
