```julia
metropolis_minmax!(tmindist, tmaxdist, lldist, acceptancedist, nsteps::Integer, dist::AbstractArray, data::AbstractArray, uncert::AbstractArray; burnin::Integer=0)
metropolis_minmax!(tmindist, tmaxdist, t0dist, lldist, acceptancedist, nsteps::Integer, dist::Collection, analyses::Collection{<:UPbAnalysis}; burnin::Integer=0)
```

In-place (non-allocating) version of `metropolis_minmax`, filling existing arrays

Run a Metropolis sampler to estimate the extrema of a finite-range source distribution `dist` using samples drawn from that distribution – e.g., estimate zircon saturation and eruption ages from a distribution of zircon crystallization ages.

### Examples

```julia
metropolis_minmax!(tmindist, tmaxdist, lldist, acceptancedist, 2*10^5, MeltsVolcanicZirconDistribution, mu, sigma, burnin=10^5)
```
