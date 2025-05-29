```
getDefaultStopTime(md::fmi2ModelDescription)
```

Returns stopTime from DefaultExperiment if defined else defaults to nothing.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Returns

  * `md.defaultExperiment.stopTime::Union{Real,Nothing}`: Returns a real value `stopTime` from the DefaultExperiment if defined else defaults to `nothing`.
