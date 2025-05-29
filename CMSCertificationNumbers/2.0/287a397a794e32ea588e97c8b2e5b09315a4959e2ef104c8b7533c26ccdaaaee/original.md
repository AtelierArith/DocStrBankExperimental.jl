```
infer_ccn_type(s) -> T<:CCN
```

Infer the type of the CCN from a string in canonical CCN format.

# Arguments

  * `s::Union{AbstractString,Integer}` - A string or integer value in canonical CCN format.

# Return value

The inferred type, which will be a subtype of `CCN`. Throws if the type cannot be inferred from `s`.

See also [`clean_ccn`](@ref) to canonicalize a CCN string.
