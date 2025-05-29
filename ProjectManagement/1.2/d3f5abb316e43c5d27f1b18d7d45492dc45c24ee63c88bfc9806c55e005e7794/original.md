```
critical_path([f=mean], proj::Project)
```

Computes the critical path though the project. This is the path who's duration determines the completion time of the project.

You may pass in a function `f` to transform the duration when computing the cost. By default it uses `mean`, but for example you can assume everything is worst case using `path_durations(maximum, proj)`; or you could   compute the path length in terms of number of tasks using `path_durations(x->1, proj)`.

See also [`path_durations`](@ref).
