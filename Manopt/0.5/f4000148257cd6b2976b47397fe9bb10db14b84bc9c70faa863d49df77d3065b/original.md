```
decorate_objective!(M, o::AbstractManifoldObjective)
```

decorate the [`AbstractManifoldObjective`](@ref)`o` with specific decorators.

# Optional arguments

optional arguments provide necessary details on the decorators. A specific one is used to activate certain decorators.

  * `cache=missing`: specify a cache. Currently `:Simple` is supported and `:LRU` if you load [`LRUCache.jl`](https://github.com/JuliaCollections/LRUCache.jl). For this case a tuple specifying what to cache and how many can be provided, has to be specified. For example `(:LRU, [:Cost, :Gradient], 10)` states that the last 10 used cost function evaluations and gradient evaluations should be stored. See [`objective_cache_factory`](@ref) for details.
  * `count=missing`: specify calls to the objective to be called, see [`ManifoldCountObjective`](@ref) for the full list
  * `objective_type=:Riemannian`: specify that an objective is `:Riemannian` or `:Euclidean`. The `:Euclidean` symbol is equivalent to specifying it as `:Embedded`, since in the end, both refer to converting an objective from the embedding (whether its Euclidean or not) to the Riemannian one.

# See also

[`objective_cache_factory`](@ref)
