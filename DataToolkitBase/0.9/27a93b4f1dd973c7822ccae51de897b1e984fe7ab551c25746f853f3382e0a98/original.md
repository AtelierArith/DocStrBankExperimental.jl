```
fromspec(::Type{DataCollection}, spec::Dict{String, Any};
         path::Union{String, Nothing}=nothing, mod::Module=Base.Main)
```

Create a `DataCollection` from `spec`.

The `path` and `mod` keywords are used as the values for the corresponding fields in the DataCollection.
