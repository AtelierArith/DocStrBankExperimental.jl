```
precompile_reaction(rdict::Dict{String, Type}, classname::AbstractString; logger=Logging.NullLogger())
precompile_reaction(ReactionType::Type{<:AbstractReaction}; logger=Logging.NullLogger())
```

@PrecompileTools.compile*workloadで使用する: Reactionを作成し、register*メソッドを呼び出す
