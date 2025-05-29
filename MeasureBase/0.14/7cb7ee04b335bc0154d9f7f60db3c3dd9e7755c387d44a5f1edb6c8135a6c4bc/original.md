```
unsafe_logdensityof(m, x)
```

Compute the log-density of the measure `m` at `x` relative to `rootmeasure(m)`. This is "unsafe" because it does not check `insupport(m, x)`.

See also `logdensityof`.
