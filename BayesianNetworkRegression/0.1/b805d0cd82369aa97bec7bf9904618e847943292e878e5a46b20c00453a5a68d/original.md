```
Fit!(X::AbstractArray{T}, y::AbstractVector{U}, R; η=1.01,V=30,ζ=1.0,ι=1.0,aΔ=1.0,bΔ=1.0, 
     ν=10, nburn=30000, nsamples=20000, maxburn=50000, mingen=0, maxgen=0, psrf_cutoff=1.01, x_transform=true, suppress_timer=false, 
     num_chains=2, seed=nothing, purge_burn=nothing, filename="parameters.log") where {T,U}
```

Fit the Bayesian Network Regression model. There are two alternative schemes governing the number of generations. 

  * In the "traditional" scheme, the algorithm generates `nsamp` Gibbs samples after `nburn` burn-in are discarded.
  * In the "doubling generation" scheme, the algorithm generates `mingen` samples and discards the first half. If the Gelman-Rubin PSRF cutoff is not achieved, `mingen` additional samples will be generated (now considering the first half of all generations as burn-in) until either convergence is achieved or `maxgen` samples are generated.

By default, the traditional scheme is used. If valid values for `mingen` and `maxgen` are supplied then then "doubling generation" scheme will be used.

Road map of fit!:

  * Calls [`generate_samples!`](@ref) for "traditional" scheme or [`generate_samples_dbl!`](@ref) for "doubling generation" scheme directly
  * `generate_samples!` calls [`initialize_and_run!`](@ref) on every chain
  * `initialize_and_run!` calls [`initialize_variables!`](@ref) and [`gibbs_sample!`](@ref)

# Arguments

  * `X`: matrix, required, matrix of unweighted symmetric adjacency matrices to be used as predictors. Two options:        2D matrix with each row the upper triangle of the adjacency matrix associated with one sample       1D matrix with each row the adjacency matrix relating the nodes to one another
  * `y`: vector, required, vector of response variables
  * `R`: integer, required, the dimensionality of the latent variables u, a hyperparameter
  * `η`: float, default=1.01, hyperparameter used for sampling the 0 value of the πᵥ parameter, must be > 1
  * `ζ`: float, default=1.0, hyperparameter used for sampling θ
  * `ι`: float, default=1.0, hyperparameter used for sampling θ
  * `aΔ`: float, default=1.0, hyperparameter used for sampling Δ
  * `bΔ`: float, default=1.0, hyperparameter used for sampling Δ
  * `ν`: integer, default=10, hyperparameter used for sampling M, must be > R
  * `nburn`: integer, default=30000, number of burn-in samples to generate and discard
  * `nsamples`: integer, default=20000, number of Gibbs samples to generate after burn-in
  * `mingen`: integer, default 0, for "doubling generation" the minimum total number of samples to generate (burn-in + retained)
  * `maxgen`: integer, default 0, for "doubling generation" the maximum total number of samples to generate (burn-in + retained)
  * `psrf_cutoff`: float, defalut=1.2, value at which convergence is determined to have been achieved
  * `x_transform`: boolean, default=true, set to false if X has been pre-transformed into one row per sample. Otherwise the X will be transformed automatically.
  * `suppress_timer`: boolean, default=false, set to true to suppress "progress meter" output
  * `num_chains`: integer, default=2, number of separate sampling chains to run (for checking convergence)
  * `seed`: integer, default=nothing, random seed used for repeatability
  * `purge_burn`: integer, default=nothing, if set must be less than the number of burn-in samples (and ideally burn-in is a multiple of this value). After how many burn-in samples to delete previous burn-in samples.
  * `filename`: logfile with the parameters used for the fit, default="parameters.log". The file will be overwritten if a new name is not specified.

# Returns

`Results` object with the state table from the first chain and PSRF r-hat values for  γ and ξ 
