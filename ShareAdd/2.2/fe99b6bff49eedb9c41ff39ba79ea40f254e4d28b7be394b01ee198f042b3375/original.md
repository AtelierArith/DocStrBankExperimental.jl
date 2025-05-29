```
mutable struct EnvInfo
EnvInfo(name::AbstractString) -> EnvInfo
```

  * `name::String` - name of the environment
  * `path::String` - path of the environment's folder
  * `pkgs::Set{String}` - list of packages in the environment
  * `in_path::Bool` - whether the environment is in `LOAD_PATH`
  * `standard_env::Bool = false` - if the env is the standard one (which is in the `v1.11` folder for Julia v1.11)
  * `shared::Bool = true` - if shared env
  * `temporary::Bool = false` - if temporary env
  * `active_project::Bool = false` - if active project

# Examples

```julia-repl
julia> ShareAdd.EnvInfo("@DocumenterTools")
ShareAdd.EnvInfo("DocumenterTools", "/Users/eben60/.julia/environments/DocumenterTools", Set(["DocumenterTools"]), false, false, true, false, false)
```

This type is public, not exported.
