```
Logbook()
Logbook(S::LittleDict)
```

A log for statistics intended for use on every iteration of an algorithm. The logbook is constructed from a `LittleDict` ordered dictionary which maps stat names (strings) to callables, such that *statname* $i$ can be computed from *callable* $i$.

The resulting `Logbook` contains:

  * `S::LittleDict`: The ordered dict of stat names and callables
  * `records::AbstractVector`: A vector of NamedTuples where each field is a statistic.

If no argument is passed, the logbook is constructed with a set of commonly statistics such as minimum, mean, median, maximum and standard deviation; in that order.
