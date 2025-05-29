```
repetitive_heuristic(distmat::Matrix, heuristic::Function, repetitive_kw::Symbol; keywords...)
```

For each `i` in `1:n`, run `heuristic` with keyword `repetitive_kw` set to `i`. Return the tuple `(bestpath, bestcost)`. By default, `repetitive_kw` is `:firstcity`, which is appropriate for the `farthest_insertion`, `cheapest_insertion`, and `nearest_neighbor` heuristics.

Any keywords passed to `repetitive_heuristic` are passed along to each call of `heuristic`. For example, `repetitive_heuristic(dm, nearest_neighbor; do2opt = true)` will perform 2-opt for each of the `n` nearest neighbor paths.

!!! note
    The repetitive heuristic calls are parallelized with threads. For optimum speed make sure Julia is running with multiple threads.

