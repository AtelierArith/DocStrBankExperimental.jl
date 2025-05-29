```
two_opt(distmat, path)
```

Improve `path` by doing 2-opt switches (i.e. reversing part of the path) until doing so no longer reduces the cost. Return a tuple `(improved_path, improved_cost)`.

On large problem instances this heuristic can be slow, but it is highly recommended on small and medium problem instances.

See also [`simulated_annealing`](@ref) for another path generation heuristic.
