```
octofit(
    [rng::Random.AbstractRNG],
    model::Octofitter.LogDensityModel
    target_accept::Number=0.8,
    ensemble::AbstractMCMC.AbstractMCMCEnsemble=MCMCSerial();
    adaptation,
    iterations,
    drop_warmup=true,
    max_depth=12,
    initial_samples= pathfinder ? 500 : 250_000,  # deprecated
    initial_parameters=nothing, # deprecated
    step_size=nothing,
    verbosity=2,
)
```

Sample from the posterior defined by `model` using Hamiltonian Monte Carlo with  the No U-Turn Sampler from AdvancedHMC.jl.
