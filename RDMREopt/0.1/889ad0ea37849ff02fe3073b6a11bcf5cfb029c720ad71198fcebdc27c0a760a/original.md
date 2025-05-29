```
Scenarios(
    fp::String, 
    uncertainties::AbstractVector{Uncertainty},
    metrics::AbstractVector{String};
    Nscenarios::Int=100,
    Nparallel::Int=1,
    ngens::Int=100
)
```

### Args

  * `fp::String` path to a JSON file that defines the base REopt Scenario (see [REopt docs](https://nrel.github.io/REopt.jl/stable/reopt/inputs/#Scenario) for more)
  * `uncertainties::AbstractVector{Uncertainty}` vector of [Uncertainty](@ref)s
  * `metrics::AbstractVector{String}` vector of output metrics (TODO use these for analysis tools)

### Keyword Args

  * `Nscenarios::Int` number of scenarios to sample from Latin Hypercube
  * `Nparallel::Int` number of scenarios to run in parallel (when using [Run Threaded Scenarios](@ref))
  * `ngens::Int` hyperparameter of LatinHypercubeSampling.LHCoptim, used to create Latin Hypercube of samples
