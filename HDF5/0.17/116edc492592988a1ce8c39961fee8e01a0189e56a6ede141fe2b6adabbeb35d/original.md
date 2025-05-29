```
open_group(parent::Union{File,Group}, path::AbstractString; properties...)
```

Open an existing [`Group`](@ref) at `path` under the `parent` object.

Optional keyword arguments include any keywords that that belong to [`GroupAccessProperties`](@ref).
