```
build_settings_file(
    network_file::String,
    settings_file::String="settings.json";
    kwargs...
)
```

Helper function to write a settings structure to an `io` for use with ONM from a network data structure `eng::Dict{String,<:Any}`.
