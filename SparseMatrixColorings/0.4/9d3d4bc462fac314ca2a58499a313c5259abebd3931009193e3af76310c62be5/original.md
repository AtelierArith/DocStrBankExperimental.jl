```
RandomOrder(rng=default_rng(), seed=nothing)
```

Instance of [`AbstractOrder`](@ref) which sorts vertices using a random permutation, generated from `rng` with a given `seed`.

  * If `seed = nothing`, the `rng` will never be re-seeded. Therefore, two consecutive calls to `vertices(g, order)` will give different results.
  * Otherwise, the `rng` will be re-seeded before each sample. Therefore, two consecutive calls to `vertices(g, order)` will give the same result.

!!! warning
    Do not use a seed with the `default_rng()`, otherwise you will affect the global state of your program. If you need reproducibility, create a new `rng` specifically for your `RandomOrder`. The package [StableRNGs.jl](https://github.com/JuliaRandom/StableRNGs.jl) offers random number generators whose behavior is stable across Julia versions.

