```
read_dataset(parent::Union{File,Group}, name::AbstractString)
```

Read a dataset with named `name` from `parent`. This will typically return an array. The dataset will be opened, read, and closed.

See also [`HDF5.open_dataset`](@ref), [`Base.read`](@ref)
