```julia
listcommits(
    r::GitOut.Repo;
    ...
) -> Vector{SubString{String}}
listcommits(
    r::GitOut.Repo,
    n::Union{Nothing, Integer};
    branch,
    kw...
) -> Vector{SubString{String}}

```

Returns an array of commit hashes (as strings) for the repo `r`. Additional keyword arguments are passed to [`rungit`](@ref).
