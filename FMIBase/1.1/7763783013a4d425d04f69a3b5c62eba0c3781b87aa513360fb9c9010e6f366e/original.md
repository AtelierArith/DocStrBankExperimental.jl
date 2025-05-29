```
getDefaultStartTime(md::fmi2ModelDescription)
```

Returns startTime from DefaultExperiment if defined else defaults to nothing.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Returns

  * `md.defaultExperiment.startTime::Union{Real,Nothing}`: Returns a real value `startTime` from the DefaultExperiment if defined else defaults to `nothing`.
