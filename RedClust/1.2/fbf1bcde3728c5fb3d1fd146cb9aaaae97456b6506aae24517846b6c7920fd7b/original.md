PriorHyperparamsList(; [kwargs])

Contains the prior hyperparameters for the model. It is recommended to set the values using the [`fitprior`](@ref) function. Do not set these values manually unless you know what you are doing.

# Constructor arguments

  * `δ1::Float64 = 1`: the parameter $\delta_1$.
  * `α::Float64 = 1`: the shape parameter $\alpha$ in the prior for each $\lambda_k$.
  * `β::Float64 = 1`: the rate parameter $\beta$ in the prior for each $\lambda_k$.
  * `δ2::Float64 = 1`: the parameter $\delta_2$.
  * `ζ::Float64 = 1`: the shape parameter $\zeta$ in the prior for each $\theta_{kt}$.
  * `γ::Float64 = 1`: the rate parameter $\gamma$ in the prior for each $\theta_{kt}$.
  * `η::Float64 = 1`: the shape parameter $\eta$ in the prior for $r$.
  * `σ::Float64 = 1`: the rate parameter $\sigma$ in the prior for $r$.
  * `u::Float64 = 1`: the parameter $u$ in the prior for $p$.
  * `v::Float64 = 1`: the parameter $v$ in the prior for $p$.
  * `proposalsd_r::Float64 = 1`: standard deviation of the truncated Normal proposal when sampling `r` via a Metropolis-Hastings step.
  * `K_initial::Int = 1`: initial number of clusters to start the MCMC.
  * `repulsion::Bool = true`: whether to use the repulsive component of the likelihood.
  * `maxK::Int = 0`: maxmimum number of clusters to allow. If set to 0 then no maximum is imposed.

# See also

[`fitprior`](@ref)
