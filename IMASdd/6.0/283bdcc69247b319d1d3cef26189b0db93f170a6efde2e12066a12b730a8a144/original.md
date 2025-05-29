```
Base.resize!(@nospecialize(ids::IDSvector{T}), condition::Pair{String}, conditions::Pair{String}...; wipe::Bool=true, error_multiple_matches::Bool=true) where {T<:IDSvectorElement}
```

Resize if a set of conditions are not met.

If wipe=true and an entry matching the condition is found, then the content of the matching IDS is emptied.

Either way, the IDS is populated with the conditions.

NOTE: `error_multiple_matches` will delete all extra entries matching the conditions.

Returns the selected IDS
