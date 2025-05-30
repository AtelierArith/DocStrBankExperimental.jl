```
damas(env::Environment, b [,f<:AbstractArray, ω::Real]; maxiter=10)
```

Performs exactly `maxiter` DAMAS iterations for all frequency bins in `env.fn` or frequencies in `f`. `f` must contain values that match exact a (sub)set of the values in `env.fn`. Successive Over Relaxation (SOR) can be set with relaxation parameter `ω`. Default is `ω=1` corresponding to no relaxation.

# References:

Brooks, T. F. et al. (2006). A deconvolution approach for the mapping of acoustic sources (DAMAS) determined from phased microphone arrays. J.Sound.Vib. 294(4), 856–879. https://doi.org/10.1016/j.jsv.2005.12.046
