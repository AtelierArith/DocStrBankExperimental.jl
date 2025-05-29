```julia
dynamichmc_inference(
    problem,
    algorithm,
    t,
    data,
    parameter_priors;
    ...
)
dynamichmc_inference(
    problem,
    algorithm,
    t,
    data,
    parameter_priors,
    parameter_transformations;
    σ_priors,
    sample_u0,
    rng,
    num_samples,
    AD_gradient_kind,
    save_idxs,
    solve_kwargs,
    mcmc_kwargs
)

```

Run MCMC for an ODE problem. Return a `NamedTuple`, which is similar to the one returned by `DynamicHMC.mcmc_with_warmup`, with an added field `posterior` which contains a vector of posterior values (transformed from `ℝⁿ`).

# Arguments

  * `problem` is the ODE problem
  * `algorithm` is the ODE algorithm
  * `t` is the time values at which the solution is compared to `data`
  * `data` is a matrix of data, with one column for each element in `t`
  * `parameter_priors` is an iterable with the length of the number of paramers, and is used as a prior on it, should have comparable structure.
  * `parameter_transformations`: a `TransformVariables` transformation to mapping `ℝⁿ` to the vector of valid parameters.

# Keyword arguments

  * `rng` is the random number generator used for MCMC. Defaults to the global one.
  * `num_samples` is the number of MCMC draws (default: 1000)
  * `AD_gradient_kind` is passed on to `LogDensityProblems.ADgradient`, make sure to `import` the corresponding library.
  * `solve_kwargs` is passed on to `solve`
  * `mcmc_kwargs` are passed on as keyword arguments to `DynamicHMC.mcmc_with_warmup`
