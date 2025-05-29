```
bind_my_artifact!(artifacts_toml::String, name::AbstractString, hash::SHA256; force::Bool = false, metadata = nothing)
```

Writes a mapping of `name` -> `hash` in the given "Artifacts.toml" file and track the usage. If `force`  is set to `true`, this will overwrite a pre-existant mapping, otherwise an error is raised. By setting  `metadata`, we can store extra information in the `artifacts_toml` with field name `meta` of `name` entry.
