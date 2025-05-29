```
CollectionVersionMismatch(version::Int)
```

The `version` of the collection currently being acted on is not supported by the current version of DataToolkitBase.

# Example occurrence

```julia-repl
julia> fromspec(DataCollection, SmallDict{String, Any}("data_config_version" => -1))
ERROR: CollectionVersionMismatch: -1 (specified) ≠ 0 (current)
  The data collection specification uses the v-1 data collection format, however
  the installed DataToolkitBase version expects the v0 version of the format.
  In the future, conversion facilities may be implemented, for now though you
  will need to manually upgrade the file to the v0 format.
Stacktrace: [...]
```
