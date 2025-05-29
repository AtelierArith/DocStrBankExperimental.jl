```
getValueReferencesAndNames(obj; vrs=md.valueReferences)
```

with:

obj ∈ (fmi2ModelDescription, FMU2)

Returns a dictionary `Dict(fmi2ValueReference, Array{String})` of value references and their corresponding names.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Keywords

  * `vrs=md.valueReferences`: Additional attribute `valueReferences::Array{fmi2ValueReference}` of the Model Description that  is a handle to a (base type) variable value. Handle and base type uniquely identify the value of a variable. (default = `md.valueReferences::Array{fmi2ValueReference}`)

# Returns

  * `dict::Dict{fmi2ValueReference, Array{String}}`: Returns a dictionary that constructs a hash table with keys of type fmi2ValueReference and values of type Array{String}.
