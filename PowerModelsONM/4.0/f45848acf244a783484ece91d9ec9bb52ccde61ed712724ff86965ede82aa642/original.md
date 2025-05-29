```
set_setting!(args::Dict{String,<:Any}, path::Tuple{Vararg{String}}, value::Any)
```

Helper function to set an option at `path` to `value` and then regenerate the multinetwork data from `args`.
