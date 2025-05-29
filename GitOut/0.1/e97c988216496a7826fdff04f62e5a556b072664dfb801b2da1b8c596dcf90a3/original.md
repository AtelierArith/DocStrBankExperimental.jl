```julia
remotenames(
    r::GitOut.Repo;
    kw...
) -> Vector{SubString{String}}

```

Retrieve a list of remotes by name as an `AbstractVector` of `AbstractString`.  Additional keyword arguments are passed to [`rungit`](@ref).
