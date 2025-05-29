```julia
add(
    r::GitOut.Repo,
    pathspec::AbstractVector;
    force,
    interactive,
    edit,
    all,
    kw...
) -> GitOut.Repo

```

Add file contents to the index of repository `r`. Additional keyword arguments are passed to [`rungit`](@ref).
