```julia
getremoteurl(
    r::GitOut.Repo,
    name::AbstractString;
    kw...
) -> Any

```

Get the URL for the remote of repo `r` named `name`.  Additional keyword arguments are passed to [`rungit`](@ref).
