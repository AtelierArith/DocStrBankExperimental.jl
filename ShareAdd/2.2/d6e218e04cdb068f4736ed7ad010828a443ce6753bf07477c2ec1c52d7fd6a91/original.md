```
mutable struct PackageInfo
```

  * `name::String` - name of the package
  * `envs::Vector{EnvInfo}` - list of environments in which the package is present
  * `in_path::Bool` - whether any of the environments is in `LOAD_PATH`

This type is public, not exported.
