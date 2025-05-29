```
parametricbootstrap([rng::AbstractRNG], nsamp::Integer, m::MixedModel{T}, ftype=T;
    β = fixef(m), σ = m.σ, θ = m.θ, progress=true, optsum_overrides=(;))
```

Perform `nsamp` parametric bootstrap replication fits of `m`, returning a `MixedModelBootstrap`.

The default random number generator is `Random.GLOBAL_RNG`.

`ftype` can be used to store the computed bootstrap values in a lower precision. `ftype` is not a named argument because named arguments are not used in method dispatch and thus specialization. In other words, having `ftype` as a positional argument has some potential performance benefits.

# Keyword Arguments

  * `β`, `σ`, and `θ` are the values of `m`'s parameters for simulating the responses.
  * `σ` is only valid for `LinearMixedModel` and `GeneralizedLinearMixedModel` for

families with a dispersion parameter.

  * `progress` controls whether the progress bar is shown. Note that the progress

bar is automatically disabled for non-interactive (i.e. logging) contexts.

  * `optsum_overrides` is used to override values of [OptSummary](@ref) in the models

fit during the bootstrapping process. For example, `optsum_overrides=(;ftol_rel=1e-08)` reduces the convergence criterion, which can greatly speed up the bootstrap fits. Taking advantage of this speed up to increase `n` can often lead to better estimates of coverage intervals.

!!! note
    All coefficients are bootstrapped. In the rank deficient case, the inestimatable coefficients are treated as -0.0 in the simulations underlying the bootstrap, which will generally result in their estimate from the simulated data also being being inestimable and thus set to -0.0. **However this behavior may change in future releases to explicitly drop the extraneous columns before simulation and thus not include their estimates in the bootstrap result.**

