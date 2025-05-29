```julia
metropolis_min(nsteps::Integer, dist::Collection, data::Collection{<:Measurement}; burnin::Integer=0, t0prior=Uniform(0,minimum(value.(age68.(analyses)))), lossprior=Uniform(0,100))
metropolis_min(nsteps::Integer, dist::Collection, mu::AbstractArray, sigma::AbstractArray; burnin::Integer=0)
metropolis_min(nsteps::Integer, dist::Collection, analyses::Collection{<:UPbAnalysis; burnin::Integer=0)
```

Run a Metropolis sampler to estimate the minimum of a finite-range source distribution `dist` using samples drawn from that distribution – e.g., estimate zircon eruption ages from a distribution of zircon crystallization ages.

### Examples

```julia
tmindist = metropolis_min(2*10^5, MeltsVolcanicZirconDistribution, mu, sigma, burnin=10^5)

tmindist, t0dist = metropolis_min(2*10^5, HalfNormalDistribution, analyses, burnin=10^5)
```
