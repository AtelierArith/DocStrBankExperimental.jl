```
PEtabModel(sys, observables::Dict{String, PEtabObservable}, measurements::DataFrame,
           parameters::Vector{PEtabParameter}; kwargs...)
```

From a `ReactionSystem` or an `ODESystem` model, `observables` that link the model to `measurements` and `parameters` to estimate, create a `PEtabModel` for parameter estimation.

For examples on how to create a `PEtabModel`, see the documentation.

See also [`PEtabObservable`](@ref), [`PEtabParameter`](@ref), and [`PEtabEvent`](@ref).

## Keyword Arguments

  * `simulation_conditions = nothing`: An optional dictionary specifying initial specie values   and/or model parameters for each simulation condition. Only required if the model has   multiple simulation conditions.
  * `events = nothing`: Optional model events (callbacks) provided as `PEtabEvent`. Multiple   events should be provided as a `Vector` of `PEtabEvent`.
  * `verbose::Bool = false`: Whether to print progress while building the `PEtabModel`.

```
PEtabModel(path_yaml; kwargs...)
```

Import a PEtab problem in the standard format with YAML file at `path_yaml` into a `PEtabModel` for parameter estimation.

For examples on how to import a PEtab problem, see the documentation.

## Keyword Arguments

  * `ifelse_to_callback::Bool = true`: Whether to rewrite `ifelse` (SBML piecewise)   expressions to [callbacks](https://github.com/SciML/DiffEqCallbacks.jl). This improves   simulation runtime. It is strongly recommended to set this to `true`.
  * `verbose::Bool = false`: Whether to print progress while building the `PEtabModel`.
  * `write_to_file::Bool = false`: Whether to write the generated Julia functions to files in  the same directory as the PEtab problem. Useful for debugging.
