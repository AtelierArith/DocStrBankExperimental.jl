```
open_dataset(parent::Union{File, Group}, path::AbstractString; properties...)
```

Open an existing [`HDF5.Dataset`](@ref) at `path` under `parent`

Optional keyword arguments include any keywords that that belong to [`DatasetAccessProperties`](@ref) or [`DatasetTransferProperties`](@ref).
