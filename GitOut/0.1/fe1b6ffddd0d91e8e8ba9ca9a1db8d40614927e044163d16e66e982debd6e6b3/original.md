```julia
commit(r::GitOut.Repo; ...) -> GitOut.Repo
commit(
    r::GitOut.Repo,
    pathspec::AbstractVector{<:AbstractString};
    all,
    author,
    date,
    message,
    kw...
) -> GitOut.Repo

```

Record changes to repository `r`.  Additional keyword arguments are passed to [`rungit`](@ref).
