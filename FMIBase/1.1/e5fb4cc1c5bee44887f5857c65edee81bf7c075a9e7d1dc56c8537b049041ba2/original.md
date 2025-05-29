```
fmi2GetDerivateValueReferencesAndNames(md::fmi2ModelDescription)
```

Returns a dictionary `Dict(fmi2ValueReference, Array{String})` of derivative value references and their corresponding names.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Returns

  * `dict::Dict{fmi2ValueReference, Array{String}}`: Returns a dictionary that constructs a hash table with keys of type fmi2ValueReference and values of type Array{String}. So returns a dict with (vrs, names of derivatives)

See also [`getValueReferencesAndNames`](@ref)
