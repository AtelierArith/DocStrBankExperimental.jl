```
fmi2GetStateNames(fmu::FMU2; vrs=md.stateValueReferences, mode=:first)
```

Returns names of states.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Keywords

  * `vrs=md.stateValueReferences`: Additional attribute `parameterValueReferences::Array{fmi2ValueReference}` of the Model Description that  is a handle to a (base type) variable value. Handle and base type uniquely identify the value of a variable. (default = `md.stateValueReferences::Array{fmi2ValueReference}`)
  * `mode=:first`: If there are multiple names per value reference, availabel modes are `:first` (default, pick only the first one), `:group` (pick all and group them into an array) and `:flat` (pick all, but flat them out into a 1D-array together with all other names)

# Returns

  * `names::Array{String}`: Returns a array of names corresponding to parameter value references `vrs`
