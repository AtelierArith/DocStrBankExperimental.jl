```
getOutputValueReferencesAndNames(md::fmi2ModelDescription)
```

Returns a dictionary `Dict(fmi2ValueReference, Array{String})` of value references and their corresponding names.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Keywords

  * `vrs=md.outputvalueReferences`: Additional attribute `outputvalueReferences::Array{fmi2ValueReference}` of the Model Description that is a handle to a (base type) variable value. Handle and base type uniquely identify the value of a variable. (default = `md.outputvalueReferences::Array{fmi2ValueReference}`)

# Returns

  * `dict::Dict{fmi2ValueReference, Array{String}}`: Returns a dictionary that constructs a hash table with keys of type fmi2ValueReference and values of type Array{String}.So returns a dict with (vrs, names of outputs)
