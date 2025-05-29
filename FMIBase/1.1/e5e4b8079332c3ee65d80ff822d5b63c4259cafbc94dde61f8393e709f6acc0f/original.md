```
getInputNamesAndStarts(md::fmi2ModelDescription)
```

Returns a dictionary of input variables with their starting values.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Returns

  * `dict::Dict{String, Array{fmi2ValueReferenceFormat}}`: Returns a dictionary that constructs a hash table with keys of type String and values of type fmi2ValueReferenceFormat. So returns a dict with ( `md.modelVariables[i].name::String`, `starts:: Array{fmi2ValueReferenceFormat}` ). (Creates a tuple (name, starts) for each i in inputIndices)

See also [`getStartValue`](@ref).
