```
getDefaultStepSize(md::fmi2ModelDescription)
```

Returns stepSize from DefaultExperiment if defined else defaults to nothing.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Returns

  * `md.defaultExperiment.stepSize::Union{Real,Nothing}`: Returns a real value `setpSize` from the DefaultExperiment if defined else defaults to `nothing`.
