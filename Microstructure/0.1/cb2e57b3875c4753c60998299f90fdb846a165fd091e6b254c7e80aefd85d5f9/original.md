```
run_diagnostics(
    meas::Vector{Float64},
    protocol::Protocol,
    model_start::BiophysicalModel,
    sampler::Sampler,
    draws::Vector{Int64},
    rng_seed::Int64=1,
    noise::Noisemodel=Noisemodel(),
)
```

Return chain diagnostics tested with different sampling length. This function is useful for optimizing sampler for a given model.

# References

Vehtari, A., Gelman, A., Simpson, D., Carpenter, B. and Bürkner, P.C., 2021. Rank-normalization, folding, and localization: An improved R ̂ for assessing convergence of MCMC (with discussion). Bayesian analysis, 16(2), pp.667-718.
