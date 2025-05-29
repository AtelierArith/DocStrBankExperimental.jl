```
register_e4st_dep(name, message, remote_path, args...; kwargs...)
```

See documentation for `DataDeps.DataDep` for more info, but the required fields are:

  * name - the name of the metadata.  Later, access using `datadep"<name>"` or [`get_e4st_dep`](@ref)
  * message - the message to store in metadata.  A description of where the data came from, the size, etc.
  * remote_path - where to fetch the data from.
