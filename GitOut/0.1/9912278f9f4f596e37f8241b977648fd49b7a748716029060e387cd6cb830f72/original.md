```julia
addremote(
    r::GitOut.Repo,
    name::AbstractString,
    url::AbstractString;
    fetch,
    tags,
    no_tags,
    kw...
) -> GitOut.Repo

```

Add a remote named `name` to the repo pointing to the URL `url`.  Additional keyword arguments are passed to [`rungit`](@ref).
