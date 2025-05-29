```
create_group(parent::Union{File,Group}, path::AbstractString; properties...)
```

Create a new [`Group`](@ref) at `path` under the `parent` object. Optional keyword arguments include any keywords that that belong to [`LinkCreateProperties`](@ref) or [`GroupCreateProperties`](@ref).
