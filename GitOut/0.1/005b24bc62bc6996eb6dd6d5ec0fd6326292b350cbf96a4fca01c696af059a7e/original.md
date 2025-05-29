```julia
remove(r::GitOut.Repo; ...) -> GitOut.Repo
remove(
    r::GitOut.Repo,
    pathspec::AbstractVector{<:AbstractString};
    force,
    recursive,
    kw...
) -> GitOut.Repo

```

Remove files from the working tree and the index of repository `r`. Additional keyword arguments are passed to [`rungit`](@ref).
