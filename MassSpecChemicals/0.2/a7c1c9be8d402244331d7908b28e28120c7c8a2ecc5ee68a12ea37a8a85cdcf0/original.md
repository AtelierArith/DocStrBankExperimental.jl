```
parse_chemical(name, formula; kwargs...)
parse_chemical(::Type{<: Chemical}, name::AbstractString, formula::AbstractString; kwargs...)
```

Parse chemical name and construct a chemical object. The default type is `Chemical`. `kwargs` are attributes.
