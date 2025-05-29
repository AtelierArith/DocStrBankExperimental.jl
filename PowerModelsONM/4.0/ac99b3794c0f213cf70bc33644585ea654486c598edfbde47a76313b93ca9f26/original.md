```
get_option(network::Dict{String,<:Any}, path::Tuple{Vararg{String}}, default::Any=missing)::Any
```

Helper function to get a property at an arbitrary nested path in a network dictionary, returning the default value if path does not exist.
