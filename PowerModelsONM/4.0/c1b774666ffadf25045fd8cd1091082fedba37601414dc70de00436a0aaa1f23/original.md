```
get_deprecated_properties(schema::T; deprecated_properties::Union{T,Missing}=missing)::T where T <: Dict{String,Any}
```

Recursive function to walk through a schema to discover the deprecated properties
