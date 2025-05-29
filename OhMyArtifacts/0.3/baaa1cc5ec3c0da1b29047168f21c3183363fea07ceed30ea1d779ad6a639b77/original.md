```
load_my_artifacts_toml(artifacts_toml::String)
```

Safely read the `artifacts_toml`, return a `Dict{String, Any}` of binding name to sha256 hash.
