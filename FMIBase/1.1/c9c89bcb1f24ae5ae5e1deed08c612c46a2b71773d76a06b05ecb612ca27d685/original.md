```
getNamesAndUnits(md::fmi2ModelDescription)
```

Returns a dictionary of variables with their units.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Returns

  * `dict::Dict{String, String}`: Returns a dictionary that constructs a hash table with keys of type String and values of type String. So returns a dict with ( `md.modelVariables[i].name::String`, `md.modelVariables[i]._Real.unit::Union{String, Nothing}`). (Creates a tuple (name, unit) for each i in 1:length(md.modelVariables))

See also [`getUnit`](@ref).
