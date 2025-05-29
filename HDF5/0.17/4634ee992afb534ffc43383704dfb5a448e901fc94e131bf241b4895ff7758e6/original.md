```
write_dataset(parent::Union{File,Group}, name::Union{AbstractString,Nothing}, data; pv...)
```

Create and write a dataset with `data`. Keywords are forwarded to [`create_dataset`](@ref). Providing `nothing` as the name will create an anonymous dataset.

See also [`create_dataset`](@ref)
