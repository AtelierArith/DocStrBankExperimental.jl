Adaptive MCMC sampler that makes use of gradient information. Based on Livingstone et al. (2020) The adaptation is based on Andrieu and Thoms (2008), Algorithm 4 in Section 5.

```Julia
barker_mcmc(lp,
            inits::AbstractVector;
            n_iter = 100::Int,
            σ = 2.4/(length(inits)^(1/6)),
            target_acceptance_rate = 0.4,
            κ::Float64 = 0.6,
            n_iter_adaptation = Inf,
            preconditioning::Function = BarkerMCMC.precond_eigen)
```

or

```Julia
barker_mcmc(log_p::Function, ∇log_p::Function,
            inits::AbstractVector;
            n_iter = 100::Int,
            σ = 2.4/(length(inits)^(1/6)),
            target_acceptance_rate = 0.4,
            κ::Float64 = 0.6,
            n_iter_adaptation = Inf,
            preconditioning::Function = BarkerMCMC.precond_eigen)
```

### Arguments

  * `lp`: log density object that supports the API of the `LogDensityProblems.jl` package
  * `log_p::Function`: function returning the log of the (non-normalized) density
  * `∇log_p::Function`: function returning the gradient of log of the (non-normalized) density
  * `inits::Vector`: initial starting values
  * `n_iter = 100`: number of iterations
  * `σ = 2.4/(length(inits)^(1/6))`: global scale of proposal distribution
  * `target_acceptance_rate = 0.4`: desired acceptance rate
  * `κ = 0.6`: controls adaptation speed, κ ∈ (0.5, 1). Larger values lead to slower adaptation, see Section 6.1            in Livingstone et al. (2020).
  * `n_iter_adaptation = Inf`: number of iterations with adaptation
  * `preconditioning::Function = BarkerMCMC.precond_eigen`: Either `BarkerMCMC.precond_eigen` or `BarkerMCMC.precond_cholesky`. Calculating the preconditioning matrix with a cholesky decomposition is slighly cheaper, however, the eigen value decomposition allows for a proper rotation of the proposal distribution.

### Return Value

A named tuple with fields:

  * `samples`: array containing the samples
  * `log_p`: vector containing the value of `log_p` for each sample.

### References

Andrieu, C., Thoms, J., 2008. A tutorial on adaptive MCMC. Statistics and computing 18, 343–373.

Livingstone, S., Zanella, G., 2021. The Barker proposal: Combining robustness and efficiency in gradient-based MCMC. Journal of the Royal Statistical Society: Series B (Statistical Methodology). https://doi.org/10.1111/rssb.12482
