```
sync(folder::AbstractString, all::Bool=false; kwargs...)
sync(folders::AbstractVector{<:AbstractString}, all::Bool=false; kwargs...)
sync(product::Symbol, folder::AbstractString, all::Bool=false; kwargs...)
sync(product::Symbol, folders::AbstractVector{<:AbstractString}, all::Bool=false; kwargs...)
```

Syncronize an existing archive of local granules in `folder(s)` with the latest granules available. Specifically, this will run [`search`](@ref) and [`download`](@ref) for any granules not yet present in folder(s), to the *first* folder in the list.

!!! warning
    Using sync could result in downloading significant (TB+) amounts of data.


Assumes all folders contain granules of the same product. If not, pass the product as Symbol: [`sync(::Symbol, folders, all)`](@ref) instead.

When `all` is false (the default), sync will search only for granules past the date of the latest granule found in `folders`. If true, it will search for all granules. Note that ICESat granules are not timestamped, so sync will try to download *all* ICESat granules not yet present, regardless of this setting.

Any `kwargs...` are passed to the [`search`](@ref) function. This enables sync to only download granules within a certain extent, for example.
