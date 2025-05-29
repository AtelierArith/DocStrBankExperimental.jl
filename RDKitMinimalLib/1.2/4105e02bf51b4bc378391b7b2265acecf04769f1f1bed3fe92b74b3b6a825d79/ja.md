```
get_inchi_for_molblock(molblock::AbstractString, details::Union{Dict{String,Any},Nothing}=nothing)::String
```

molblockのInChIを取得します。

```julia
inchi = get_inchi_for_molblock(molblock)
```
