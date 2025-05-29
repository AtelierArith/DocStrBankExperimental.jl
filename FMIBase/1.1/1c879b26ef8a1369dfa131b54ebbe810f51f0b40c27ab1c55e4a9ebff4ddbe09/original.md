```
getStartValue(md::fmi2ModelDescription, vrs::fmi2ValueReferenceFormat = md.valueReferences)
```

Returns the start/default value for a given value reference.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.
  * `vrs::fmi2ValueReferenceFormat = md.valueReferences`: wildcards for how a user can pass a fmi[X]ValueReference (default = md.valueReferences)

More detailed: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

# Returns

  * `starts::Array{fmi2ValueReferenceFormat}`: start/default value for a given value reference

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2: 2.2.7  Definition of Model Variables (ModelVariables)
