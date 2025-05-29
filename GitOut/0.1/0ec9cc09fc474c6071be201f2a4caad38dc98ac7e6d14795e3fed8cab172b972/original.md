```julia
pull(r::GitOut.Repo; ...) -> GitOut.Repo
pull(
    r::GitOut.Repo,
    rem::AbstractString;
    branch,
    rebase,
    depth,
    prune,
    tags,
    jobs,
    kw...
) -> GitOut.Repo

```

Fetch updates from the remote names `rem` to repository `r`. Additional keyword arguments are passed to [`rungit`](@ref).
