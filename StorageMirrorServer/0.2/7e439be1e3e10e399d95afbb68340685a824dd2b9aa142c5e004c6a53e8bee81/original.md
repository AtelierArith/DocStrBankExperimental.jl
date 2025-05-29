```
read_packages(registry::AbstractString; kwargs...)
read_packages(f, registry; recursive=true, kwargs...)
```

Read all packages stored in registry `registry`.

If predicate function `f` is given, package that satisfies `f(pkg)==true` is put into the return list. If `recursive==true`, then all dependency packages are also added to the return list.

Kerword arguments:

  * `latest_versions_num::Integer`: only get the latest `latest_versions_num` versions for each package.
  * `fetch_full_registry::Bool = false`: `true` to disable incremental parsing.

# Examples

List all packages:

```julia
pkgs = read_packages("General")
```

List only packages under JuliaArrays:

```julia
pkgs = read_packages("General") do pkg
    occursin("JuliaArrays", pkg.url)
end
```
