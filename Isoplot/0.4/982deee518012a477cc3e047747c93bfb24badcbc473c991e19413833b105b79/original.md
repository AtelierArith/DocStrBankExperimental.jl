```julia
metropolis_min!(tmindist::DenseArray, dist::Collection, mu::AbstractArray, sigma::AbstractArray; burnin::Integer=0)
metropolis_min!(tmindist::DenseArray, t0dist::DenseArray, dist::Collection, analyses::Collection{<:UPbAnalysis}; burnin::Integer=0) where {T}
```

In-place (non-allocating) version of `metropolis_min`, fills existing array `tmindist`.

Run a Metropolis sampler to estimate the minimum of a finite-range source distribution `dist` using samples drawn from that distribution – e.g., estimate zircon eruption ages from a distribution of zircon crystallization ages.

### Examples

```julia
metropolis_min!(tmindist, 2*10^5, MeltsVolcanicZirconDistribution, mu, sigma, burnin=10^5)
```
