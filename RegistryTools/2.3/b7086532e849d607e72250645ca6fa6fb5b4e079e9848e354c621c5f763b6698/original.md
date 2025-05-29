```
register(package_repo, pkg, tree_hash; registry, registry_fork, registry_deps, push, gitconfig)
```

Register the package at `package_repo` / `tree_hash` in `registry`. Returns a `RegEdit.RegBranch` which contains information about the registration and/or any errors or warnings that occurred.

# Arguments

  * `package_repo::AbstractString`: The git repository URL for the package to be registered. If empty, keep the stored repository URL.
  * `pkg::String`: the path of the project file for the package to be registered
  * `tree_hash::AbstractString`: the tree hash (not commit hash) of the package revision to be registered

# Keyword Arguments

  * `registry::AbstractString="https://github.com/JuliaRegistries/General"`: the git repository URL for the registry
  * `registry_fork::AbstractString=registry: the git repository URL for a fork of the registry
  * `registry_deps::Vector{String}=[]`: the git repository URLs for any registries containing   packages depended on by `pkg`
  * `subdir::AbstractString=""`: path to package within `package_repo`
  * `push::Bool=false`: whether to push a registration branch to `registry` for consideration
  * `gitconfig::Dict=Dict()`: dictionary of configuration options for the `git` command
