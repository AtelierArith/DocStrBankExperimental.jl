```
pave(S::Separator, domain::IntervalBox, eps)`
```

Find the subset of `domain` defined by the constraints specified by the separator `S`. Returns (sub)pavings `inner` and `boundary`, i.e. lists of `IntervalBox`.
