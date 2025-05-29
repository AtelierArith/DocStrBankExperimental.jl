```
massdiff(pb::Problem;T,rel)
```

Compute the difference of excess of mass of a solved initial-value problem `pb` between given time `T` and initial time.

Keyword argument `T` is optional, the last computed time is used by default.

If keyword argument `rel=true` (default is false), then compute the relative difference (with initial value as reference).
