```
gevfitbayes(..., niter::Int=5000, warmup::Int=2000)
```

Generate a sample from the GEV parameters' posterior distribution.

# Arguments

  * `niter::Int = 5000`: The total number of MCMC iterations.
  * `warmup::Int = 2000`: The number of warmup iterations (burn-in).

# Implementation

The function uses the No-U-Turn Sampler (NUTS; [Hoffman and Gelman, 2014](http://jmlr.org/papers/v15/hoffman14a.html)) implemented in the [Mamba.jl](https://mambajl.readthedocs.io/en/latest/index.html) package to generate a random sample from the posterior distribution.

Currently, only the improper uniform prior is implemented, *i.e.*

$$
f_{(β₁,β₂,β₃)}(β₁,β₂,β₃) ∝ 1,
$$

where

$$
μ = X₁ × β₁,
$$

$$
ϕ = X₂ × β₂,
$$

$$
ξ = X₃ × β₃.
$$

In the stationary case, this improper prior yields to a proper posterior if the sample size is larger than 3 ([Northrop and Attalides, 2016](https://www.jstor.org/stable/24721296?seq=1)).

The covariates are standardized before estimating the parameters to help fit the  model. They are transformed back on their original scales before returning the  fitted model.

See also [`gevfitbayes`](@ref) for the other methods, [`gevfitpwm`](@ref), [`gevfit`](@ref) and [`BlockMaxima`](@ref).

# References

Hoffman M. D. and Gelman A. (2014). The No-U-Turn sampler: adaptively setting path lengths in Hamiltonian Monte Carlo. *Journal of Machine Learning Research*, 15:1593–1623.

Paul J. Northrop P. J. and Attalides N. (2016). Posterior propriety in Bayesian extreme value analyses using reference priors. *Statistica Sinica*, 26:721-743.
