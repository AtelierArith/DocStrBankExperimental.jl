```julia
push(r::GitOut.Repo; ...) -> GitOut.Repo
push(
    r::GitOut.Repo,
    rem::AbstractString;
    branch,
    delete,
    tags,
    kw...
) -> GitOut.Repo

```

Update remotes with updates to repository `r`.  Additional keyword arguments are passed to [`rungit`](@ref).
