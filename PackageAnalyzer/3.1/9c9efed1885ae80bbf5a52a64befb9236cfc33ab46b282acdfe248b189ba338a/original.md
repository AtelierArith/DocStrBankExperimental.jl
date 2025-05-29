```
find_packages_in_manifest([path_to_manifest]; registries=reachable_registries(),
                          strict=true, warn=true)) -> Vector{PkgSource}
```

Returns `Vector{PkgSource}` associated to all of the package/version combinations stored in a Manifest.toml.

  * `path_to_manifest` defaults to `joinpath(dirname(Base.active_project()), "Manifest.toml")`
  * registries: a collection of `RegistryInstance` to look in
  * `strict` and `warn` have the same meaning as in [`find_package`](@ref).
  * Standard libraries are always skipped, without warning or errors.
