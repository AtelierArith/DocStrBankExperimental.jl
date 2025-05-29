```
build_ref(
    data::Dict{String,<:Any},
    ref_extensions::Vector{<:Function} = Vector{Function}([]))::Dict{Symbol,<:Any}
```

Builds the ref dictionary from the data dictionary. Additionally, the ref dictionary can contain the fields populated by the optional vector of `ref_extensions` functions.
