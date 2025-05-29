```
open_datatype(parent::Union{File,Group}, path::AbstractString; properties...)
```

Open an existing [`Datatype`](@ref) at `path` under the `parent` object.

Optional keyword arguments include any keywords that that belong to [`DatatypeAccessProperties`](@ref).
