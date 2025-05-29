```
unif_rand_particle_pop(n, lb, ub; rng=Random.GLOBAL_RNG)
```

Generate a population of `n` [`Particle`](@ref) individuals using a uniformly random distribution between lower bounds `lb` and upper bounds `ub`.

Both `lb` and `ub` must be arrays of the same dimensions.

# Examples

```julia
julia> unif_rand_particle_pop(3, [-1, -1], [1, 1])
3-element Vector{Particle}:
 Particle([1.0823301388655755, 0.1544036055233653], [0, 0], Inf, [1.0823301388655755, 0.1544036055233653], Inf)
 Particle([1.0718059584439532, 1.5793257162200343], [0, 0], Inf, [1.0718059584439532, 1.5793257162200343], Inf)
 Particle([1.732268523018161, 0.32172551959160556], [0, 0], Inf, [1.732268523018161, 0.32172551959160556], Inf)
```
