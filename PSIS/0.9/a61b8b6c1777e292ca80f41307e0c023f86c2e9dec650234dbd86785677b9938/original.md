```
psis(log_ratios, reff = 1.0; kwargs...) -> PSISResult
psis!(log_ratios, reff = 1.0; kwargs...) -> PSISResult
```

Compute Pareto smoothed importance sampling (PSIS) log weights [VehtariSimpson2021](@citep).

While `psis` computes smoothed log weights out-of-place, `psis!` smooths them in-place.

# Arguments

  * `log_ratios`: an array of logarithms of importance ratios, with size `(draws, [chains, [parameters...]])`, where `chains>1` would be used when chains are generated using Markov chain Monte Carlo.
  * `reff::Union{Real,AbstractArray}`: the ratio(s) of effective sample size of `log_ratios` and the actual sample size `reff = ess/(draws * chains)`, used to account for autocorrelation, e.g. due to Markov chain Monte Carlo. If an array, it must have the size `(parameters...,)` to match `log_ratios`.

# Keywords

  * `warn=true`: If `true`, warning messages are delivered
  * `normalize=true`: If `true`, the log-weights will be log-normalized so that `exp.(log_weights)` sums to 1 along the sample dimensions.

# Returns

  * `result`: a [`PSISResult`](@ref) object containing the results of the Pareto-smoothing.

A warning is raised if the Pareto shape parameter $k ≥ 0.7$. See [`PSISResult`](@ref) for details and [`PSISPlots.paretoshapeplot`](@ref) for a diagnostic plot.

# Examples

Here we smooth log importance ratios for importance sampling 30 isotropic Student $t$-distributed parameters using standard normal distributions as proposals.

```jldoctest psis; setup = :(using Random; Random.seed!(42))
julia> using Distributions

julia> proposal, target = Normal(), TDist(7);

julia> x = rand(proposal, 1_000, 1, 30);  # (ndraws, nchains, nparams)

julia> log_ratios = @. logpdf(target, x) - logpdf(proposal, x);

julia> result = psis(log_ratios)
┌ Warning: 9 parameters had Pareto shape values 0.7 < k ≤ 1. Resulting importance sampling estimates are likely to be unstable.
└ @ PSIS ~/.julia/packages/PSIS/...
┌ Warning: 1 parameters had Pareto shape values k > 1. Corresponding importance sampling estimates are likely to be unstable and are unlikely to converge with additional samples.
└ @ PSIS ~/.julia/packages/PSIS/...
PSISResult with 1000 draws, 1 chains, and 30 parameters
Pareto shape (k) diagnostic values:
                        Count       Min. ESS
 (-Inf, 0.5]  good       7 (23.3%)  959
  (0.5, 0.7]  okay      13 (43.3%)  938
    (0.7, 1]  bad        9 (30.0%)  ——
    (1, Inf)  very bad   1 (3.3%)   ——
```

If the draws were generated using MCMC, we can compute the relative efficiency using [`MCMCDiagnosticTools.ess`](@extref).

```jldoctest psis
julia> using MCMCDiagnosticTools

julia> reff = ess(log_ratios; kind=:basic, split_chains=1, relative=true);

julia> result = psis(log_ratios, reff)
┌ Warning: 9 parameters had Pareto shape values 0.7 < k ≤ 1. Resulting importance sampling estimates are likely to be unstable.
└ @ PSIS ~/.julia/packages/PSIS/...
┌ Warning: 1 parameters had Pareto shape values k > 1. Corresponding importance sampling estimates are likely to be unstable and are unlikely to converge with additional samples.
└ @ PSIS ~/.julia/packages/PSIS/...
PSISResult with 1000 draws, 1 chains, and 30 parameters
Pareto shape (k) diagnostic values:
                        Count       Min. ESS
 (-Inf, 0.5]  good       9 (30.0%)  806
  (0.5, 0.7]  okay      11 (36.7%)  842
    (0.7, 1]  bad        9 (30.0%)  ——
    (1, Inf)  very bad   1 (3.3%)   ——
```

# References

  * [VehtariSimpson2021](@cite) Vehtari et al. JMLR 25:72 (2021).
