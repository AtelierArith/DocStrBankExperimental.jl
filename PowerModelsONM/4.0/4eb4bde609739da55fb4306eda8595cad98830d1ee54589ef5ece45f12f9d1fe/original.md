```
set_options!(settings::Dict{String,<:Any}, options::Dict{Tuple{Vararg{String}},<:Any})
```

Helper function to set multiple properties in an `options` at path::Tuple{Vararg{String}} to value::Any. This does not rebuild the network data structure.
