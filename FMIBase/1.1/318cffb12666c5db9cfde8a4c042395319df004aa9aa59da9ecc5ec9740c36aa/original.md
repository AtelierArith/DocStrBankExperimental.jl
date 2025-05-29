```
getNamesAndInitials(md::fmi2ModelDescription)
```

Returns a dictionary of variables with their initials.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Returns

  * `dict::Dict{String, Cuint}`: Returns a dictionary that constructs a hash table with keys of type String and values of type Cuint. So returns a dict with ( `md.modelVariables[i].name::String`, `md.modelVariables[i].inital::Union{fmi2Initial, Nothing}`). (Creates a tuple (name,initial) for each i in 1:length(md.modelVariables))

See also [`getInitial`](@ref).
