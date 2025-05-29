Struct containing MCMC samples.

# Fields

  * `options::MCMCOptionsList`: options passed to the sampler.
  * `params::PriorHyperparamsList`: prior hyperparameters used by the sampler.
  * `clusts::Vector{ClustLabelVector}`: contains the clustering allocations. `clusts[i]` is a vector containing the clustering allocation from the `i`th sample.
  * `posterior_coclustering::Matrix{Float64}`: the posterior coclustering matrix.
  * `K::Vector{Int}`: posterior samples of $K$, i.e., the number of clusters. `K[i]` is the number of clusters in `clusts[i]`.
  * `r::Vector{Float64}`: posterior samples of the parameter $r$.
  * `p::Vector{Float64}`: posterior samples of the parameter $p$.
  * `K_mean`, `r_mean`, `p_mean`: posterior mean of `K`, `r`, and `p` respectively.
  * `K_variance`, `r_variance`, `p_variance`: posterior variance of `K`, `r`, and `p` respectively.
  * `K_acf::Vector{Float64}`, `r_acf::Vector{Float64}`, `p_acf::Vector{Float64}`: autocorrelation function for `K`, `r`, and `p` respectively.
  * `K_iac`, `r_iac`, and `p_iac`: integrated autocorrelation coefficient for `K`, `r`, and `p` respectively.
  * `K_ess::Float64`, `r_ess::Float64`, and `p_ess::Float64`: effective sample size for `K`, `r`, and `p` respectively.
  * `loglik::Vector{Float64}`: log-likelihood for each sample.
  * `logposterior::Vector{Float64}`: a function proportional to the log-posterior for each sample, with constant of proportionality equal to the normalising constant of the partition prior.
  * `splitmerge_splits`: Boolean vector indicating the iterations when a split proposal was used in the split-merge step. Has length `numMH * numiters` (see [`MCMCOptionsList`](@ref)).
  * `splitmerge_acceptance_rate`: acceptance rate of the split-merge proposals.
  * `r_acceptances`: Boolean vector indicating the iterations (including burnin and the thinned out iterations) where the Metropolis-Hastings proposal for `r` was accepted.
  * `r_acceptance_rate:`: Metropolis-Hastings acceptance rate for `r`.
  * `runtime`: total runtime for all iterations.
  * `mean_iter_time`: average time taken for each iteration.
