```
 select(y::EventSeries, t1, t2)
```

returns an EventSeries which is a subset of the input series, containing the `Event`s in the time domain [tstart, tend]. The endpoint values are set by filling forward Assumes that the input time domain `[t1, t2]` is contained in the input EventSeries.
