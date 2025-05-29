```
convert_deprecated_runtime_args!(
    runtime_args::Dict{String,<:Any},
    settings::Dict{String,<:Any},
    base_network::Dict{String,<:Any},
    timesteps::Int
)::Tuple{Dict{String,Any},Dict{String,Any}}
```

Helper function to convert deprecated runtime arguments to their appropriate network settings structure
