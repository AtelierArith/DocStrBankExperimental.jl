```
sampleplot([x::AbstractVector=f.x, ]f::FiniteGP; samples=1, kwargs...)
```

Plot samples from the projection `f` of a Gaussian process versus `x`.

!!! note
    Make sure to load [Plots.jl](https://github.com/JuliaPlots/Plots.jl) before you use this function.


When plotting multiple samples, these are treated as a *single* series (i.e., only a single entry will be added to the legend when providing a `label`).

# Example

```julia
using Plots

gp = GP(SqExponentialKernel())
sampleplot(gp(rand(5)); samples=10, linealpha=1.0)
```

The given example plots 10 samples from the projection of the GP `gp`. The `linealpha` is modified from default of 0.35 to 1.

---

```
sampleplot(x::AbstractVector, gp::AbstractGP; samples=1, kwargs...)
```

Plot samples from the finite projection `gp(x, 1e-9)` versus `x`.
