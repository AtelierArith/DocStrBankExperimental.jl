```
isModelStructureDerivativesAvailable(md::fmi2ModelDescription)
```

Returns if the FMU model description contains `dependency` information for `derivatives`.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Returns

  * `::Bool`: Returns true, if the FMU model description contains `dependency` information for `derivatives`.
