```
create_reaction(rdict::Dict{String, Type}, classname::String, name::String, external_parameters::Dict{String, Any}) -> reaction::AbstractReaction
create_reaction(ReactionType::Type{<:AbstractReaction}, name::String, external_parameters::Dict{String, Any}) -> reaction::AbstractReaction
```

Create and configure a reaction.

Sets `ReactionBase` with name, classname, external_parameters
