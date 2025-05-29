```
find_package(name_or_uuid::Union{AbstractString, UUID}; registries=reachable_registries(), version::Union{VersionNumber,Nothing}=nothing, strict=true, warn=true) -> PkgSource
```

Returns the [`PkgSource`](@ref) for the package `pkg`.

  * registries: a collection of `RegistryInstance` to look in
  * `version`: if `nothing`, finds the maximum registered version in any registry. Otherwise looks for that version number.
  * If `strict` is true, errors if the package cannot be found. Otherwise, returns `nothing`.
  * If `warn` is true, warns if the package cannot be found.

See also:  [`find_packages`](@ref).
