```
update()
update(nm::AbstractString; warn_if_missing=false)
update(nm::Vector{<:AbstractString}; warn_if_missing=true)
update(env::AbstractString, pkgs::Union{AbstractString, Vector{<:AbstractString}}; warn_if_missing=true) 
update(env::EnvInfo, pkgs::Union{Nothing, S, Vector{S}} = Nothing; warn_if_missing=false) where S <: AbstractString
update(p::Pair{<:AbstractString, <:AbstractString}; warn_if_missing=false)
```

  * Called without arguments, updates all shared environments.
  * Called with a single argument `nm::String` starting with "@", updates the shared environment `nm`.
  * Called with a single argument `nm::String` not starting with "@", updates the package `nm`    in all shared environments containing the package, as well as all it's downstream dependencies.
  * Called with a single argument `nm::Vector{String}`, updates the packages and/or environments in `nm`.
  * Called with two arguments `env` and `pkgs`, updates the package(s) `pkgs` in the environment `env`.
  * Called with an argument `env => pkg`, updates the package `pkg` in the environment `env`.

# kwarg

  * `warn_if_missing::Bool=true` - if env or pkg not found, issues a warning, otherwise would throw an error

If Julia version supports version-specific manifest, then on any updates a versioned manifest will be created in each updated env. See also [`make_current_mnf`](@ref).

Returnes `nothing`.

# Examples

```julia-repl
julia> ShareAdd.update("@StatPackages")
julia> ShareAdd.update("@Foo" => "bar")
```

This function is public, not exported.
