```
analyze_manifest([path_to_manifest]; registries=reachable_registries(),
                 auth=github_auth(), sleep=0)
```

Convienence function to run [`find_packages_in_manifest`](@ref) then [`analyze`](@ref) on the results. Positional argument `path_to_manifest` defaults to `joinpath(dirname(Base.active_project()), "Manifest.toml")`.
