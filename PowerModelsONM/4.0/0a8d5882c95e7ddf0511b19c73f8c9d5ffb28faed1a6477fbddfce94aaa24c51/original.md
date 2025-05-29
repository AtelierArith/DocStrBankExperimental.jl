```
get_setting(args::Dict{String,Any}, path::Tuple{Vararg{String}}, default::Any=missing)::Any
```

Helper function to get a property in settings at an arbitrary nested path in an `args` dictionary, returning the default value if path does not exist.
