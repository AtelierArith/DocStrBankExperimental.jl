```
find_neighbors(system; n_threads=Threads.nthreads())
find_neighbors(system, neighbor_finder, current_neighbors=nothing, step_n=0,
               force_recompute=false; n_threads=Threads.nthreads())
```

Obtain a list of close atoms in a [`System`](@ref).

Custom neighbor finders should implement this function.
