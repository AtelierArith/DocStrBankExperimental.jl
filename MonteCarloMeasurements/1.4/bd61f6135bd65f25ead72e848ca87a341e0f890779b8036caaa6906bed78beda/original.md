```
sigmapoints(m, Σ)
sigmapoints(d::Normal)
sigmapoints(d::MvNormal)
```

The [unscented transform](https://en.wikipedia.org/wiki/Unscented_transform#Sigma_points) uses a small number of points to propagate the first and second moments of a probability density, called *sigma points*. We provide a function `sigmapoints(μ, Σ)` that creates a `Matrix` of `2n+1` sigma points, where `n` is the dimension. This can be used to initialize any kind of `AbstractParticles`, e.g.:

```julia
julia> m = [1,2]

julia> Σ = [3. 1; 1 4]

julia> p = StaticParticles(sigmapoints(m,Σ))
2-element Array{StaticParticles{Float64,5},1}:
 (5 StaticParticles: 1.0 ± 1.73)
 (5 StaticParticles: 2.0 ± 2.0)

julia> cov(p) ≈ Σ
true

julia> mean(p) ≈ m
true
```

Make sure to pass the variance (not std) as second argument in case `μ` and `Σ` are scalars.

# Caveat

If you are creating several one-dimensional uncertain values using sigmapoints independently, they will be strongly correlated. Use the multidimensional constructor! Example:

```julia
p = StaticParticles(sigmapoints(1, 0.1^2))               # Wrong!
ζ = StaticParticles(sigmapoints(0.3, 0.1^2))             # Wrong!
ω = StaticParticles(sigmapoints(1, 0.1^2))               # Wrong!

p,ζ,ω = StaticParticles(sigmapoints([1, 0.3, 1], 0.1^2)) # Correct
```
