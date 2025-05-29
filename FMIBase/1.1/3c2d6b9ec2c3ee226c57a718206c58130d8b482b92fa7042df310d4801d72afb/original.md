```
getDefaultTolerance(md::fmi2ModelDescription)
```

Returns tolerance from DefaultExperiment if defined else defaults to nothing.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Returns

  * `md.defaultExperiment.tolerance::Union{Real,Nothing}`: Returns a real value `tolerance` from the DefaultExperiment if defined else defaults to `nothing`.
