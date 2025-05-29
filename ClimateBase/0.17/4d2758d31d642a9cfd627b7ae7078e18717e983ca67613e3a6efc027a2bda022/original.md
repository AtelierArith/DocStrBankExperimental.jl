```
sametimespan(Xs; mintime = nothing, maxtime = nothing) → Ys
```

Given a container of `ClimArray`s, return the same `ClimArray`s but now accessed in the `Time` dimension so that they all span the same time interval. Also works for dictionaries with values `ClimArray`s.

Optionally you can provide `Date` or `DateTime` values for the keywords `mintime, maxtime` that can further limit the minimum/maximum time span accessed.

`sametimespan` takes into consideration the temporal sampling of the arrays for better accuracy.
