```
getModelVariableIndices(md::fmi2ModelDescription; vrs=md.valueReferences)
```

Returns a array of indices corresponding to value references `vrs`

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Keywords

  * `vrs=md.valueReferences`: Additional attribute `valueReferences::Array{fmi2ValueReference}` of the Model Description that  is a handle to a (base type) variable value. Handle and base type uniquely identify the value of a variable. (default = `md.valueReferences::Array{fmi2ValueReference}`)

# Returns

  * `names::Array{Integer}`: Returns a array of indices corresponding to value references `vrs`
