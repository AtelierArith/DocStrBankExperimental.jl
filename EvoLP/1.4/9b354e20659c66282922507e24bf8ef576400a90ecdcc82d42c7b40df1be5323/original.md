```
normal_rand_particle_pop(n, μ, Σ; rng=Random.GLOBAL_RNG)
```

Generate a population of `n` [`Particle`](@ref) using a normal distribution with means `μ``and covariance`Σ`.

`μ` expects a vector of length *l* (i.e. number of dimensions) while `Σ` expects an *l x l* matrix of covariances.

# Examples

```julia
julia> normal_rand_particle_pop(3, [0, 0], [1 0; 0 1])
3-element Vector{Particle}:
 Particle([-0.6025996585348097, -1.0055548956861133], [0.0, 0.0], Inf, [-0.6025996585348097, -1.0055548956861133], Inf)
 Particle([-0.7562454555135321, 1.9490439959687778], [0.0, 0.0], Inf, [-0.7562454555135321, 1.9490439959687778], Inf)
 Particle([0.5687241357408321, -0.7406267072113427], [0.0, 0.0], Inf, [0.5687241357408321, -0.7406267072113427], Inf)
```
