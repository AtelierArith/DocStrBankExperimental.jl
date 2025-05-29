```
get_variable(
    method::AbstractReactionMethod, localname::AbstractString; 
    allow_not_found=false
) -> v
```

Get a single VariableReaction `v` by `localname`.

If `localname` not present, returns `nothing` if `allow_not_found==true` otherwise errors.
