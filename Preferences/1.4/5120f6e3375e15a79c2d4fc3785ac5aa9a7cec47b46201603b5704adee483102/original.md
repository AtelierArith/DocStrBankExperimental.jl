```
load_preference(uuid_or_module_or_name, key, default = nothing)
```

Load a particular preference from the `Preferences.toml` file, shallowly merging keys as it walks the hierarchy of load paths, loading preferences from all environments that list the given UUID as a direct dependency.

Most users should use the `@load_preference` convenience macro which auto-determines the calling `Module`.
