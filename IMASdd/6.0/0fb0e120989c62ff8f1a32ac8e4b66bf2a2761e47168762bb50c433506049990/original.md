```
resize!(
    @nospecialize(ids::IDSvector{T}),
    identifier_name::Symbol,
    conditions::Pair{String}...;
    wipe::Bool=true,
    error_multiple_matches::Bool=true
)::T where {T<:IDSvectorElement}
```

Resize ids if `identifier_name` is not found based on `index` of `index_2_name(ids)` and a set of conditions are not met.

If wipe=true and an entry matching the condition is found, then the content of the matching IDS is emptied.

Either way, the IDS is populated with the conditions.

NOTE: `error_multiple_matches` will delete all extra entries matching the conditions.

Returns the selected IDS
