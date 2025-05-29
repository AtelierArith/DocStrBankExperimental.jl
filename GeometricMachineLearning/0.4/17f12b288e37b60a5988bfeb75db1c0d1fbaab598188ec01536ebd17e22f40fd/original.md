```
DataLoader(dl, backend)
```

Make a new instance of `DataLoader` based on an existing instance of `DataLoader` for a new `backend`.

This allocates new memory of the same size as is used for the original `dl` and then copies the data.

By default the data type remains unchanged, i.e. `eltype(DataLoader(dl, backend)) == eltype(dl)` is `true`.

If you want to change the data type write e.g. 

```julia
    DataLoader(dl, backend, Float32)
```

# Arguments

There is an optional keyword argument 

  * `autoencoder = nothing`.

By default this inherits the autoencoder property form `dl`.

See the docstring for [`DataLoader(data::AbstractArray{<:Number, 3})`](@ref).
