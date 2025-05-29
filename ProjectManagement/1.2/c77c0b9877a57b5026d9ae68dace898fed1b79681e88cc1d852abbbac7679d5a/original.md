```
path_durations([f=mean], proj::Project)
```

Compute the duration of every path of tasks with in the project. They are returned as a vector of pairs: `path => cost`, sorted by cost (descending). Thus the first is the critical path, and the last is the least critical path.

You may pass in a function `f` to transform the duration when computing the cost. By default it uses `mean`, but for example you can assume everything is worst case using `path_durations(maximum, proj)`; or you could   compute the path length in terms of number of tasks using `path_durations(x->1, proj)`.

See also [`critical_path`](@ref).
