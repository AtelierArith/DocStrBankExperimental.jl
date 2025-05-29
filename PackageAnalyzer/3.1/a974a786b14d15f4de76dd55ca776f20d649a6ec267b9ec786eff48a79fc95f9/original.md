```
find_packages(; registries=reachable_registries())) -> Vector{PkgSource}
find_packages(names::AbstractString...; registries=reachable_registries()) -> Vector{PkgSource}
find_packages(names; registries=reachable_registries()) -> Vector{PkgSource}
```

Find all packages in the given registry (specified by the `registry` keyword argument), the [General](https://github.com/JuliaRegistries/General) registry by default. Return a vector of [`PkgSource`](@ref) pointing to to the directories of each package in the registry.

Pass a list of package `names` as the first argument to return the paths corresponding to those packages, or individual package names as separate arguments.
