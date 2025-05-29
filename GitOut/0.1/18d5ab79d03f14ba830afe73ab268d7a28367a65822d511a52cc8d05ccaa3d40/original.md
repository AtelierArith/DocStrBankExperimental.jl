```julia
clone(
    url::URIs.URI,
    path::AbstractString;
    kw...
) -> GitOut.Repo

```

Clone the git repo from remote at `url` to path `path`.  Additional keyword arguments are passed to [`rungit`](@ref).
