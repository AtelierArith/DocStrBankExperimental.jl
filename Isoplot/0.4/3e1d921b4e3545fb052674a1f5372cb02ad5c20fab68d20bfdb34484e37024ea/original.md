```julia
metropolis_minmax(nsteps::Integer, dist::Collection, data::Collection{<:Measurement}; burnin::Integer=0)
metropolis_minmax(nsteps::Integer, dist::AbstractArray, data::AbstractArray, uncert::AbstractArray; burnin::Integer=0)
```

Run a Metropolis sampler to estimate the extrema of a finite-range source distribution `dist` using samples drawn from that distribution – e.g., estimate zircon saturation and eruption ages from a distribution of zircon crystallization ages.

### Examples

```julia
tmindist, tmaxdist, lldist, acceptancedist = metropolis_minmax(2*10^5, MeltsVolcanicZirconDistribution, mu, sigma, burnin=10^5)
```
