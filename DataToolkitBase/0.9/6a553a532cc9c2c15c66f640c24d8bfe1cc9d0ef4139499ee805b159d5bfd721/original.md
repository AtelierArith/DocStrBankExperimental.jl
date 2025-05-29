```
loadcollection!(source::Union{<:AbstractString, <:IO}, mod::Module=Base.Main;
                soft::Bool=false, index::Int=1)
```

Load a data collection from `source` and add it to the data stack at `index`. `source` must be accepted by `read(source, DataCollection)`.

`mod` should be set to the Module within which `loadcollection!` is being invoked. This is important when code is run by the collection. As such, it is usually appropriate to call:

```julia
loadcollection!(source, @__MODULE__; soft)
```

When `soft` is set, should an data collection already exist with the same UUID, nothing will be done and `nothing` will be returned.
