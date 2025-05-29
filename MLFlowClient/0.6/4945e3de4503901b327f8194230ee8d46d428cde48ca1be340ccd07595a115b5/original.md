```
refresh(instance::MLFlow, run::Run)
refresh(instance::MLFlow, experiment::Experiment)
```

Get the latest metadata for a [`Run`](@ref) or [`Experiment`](@ref).

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `run` or `experiment`: [`Run`](@ref) or [`Experiment`](@ref) to refresh.

# Returns

An instance of type [`Run`](@ref) or [`Experiment`](@ref).
