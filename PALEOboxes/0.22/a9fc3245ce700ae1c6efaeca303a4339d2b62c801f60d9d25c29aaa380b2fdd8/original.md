```
precompile_reaction(rdict::Dict{String, Type}, classname::AbstractString; logger=Logging.NullLogger())
precompile_reaction(ReactionType::Type{<:AbstractReaction}; logger=Logging.NullLogger())
```

For use in @PrecompileTools.compile*workload: create Reaction and call register*methods
