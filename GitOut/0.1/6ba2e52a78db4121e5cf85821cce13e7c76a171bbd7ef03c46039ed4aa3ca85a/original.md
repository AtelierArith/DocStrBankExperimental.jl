```julia
remotes(
    r::GitOut.Repo;
    kw...
) -> Union{OrderedCollections.OrderedDict{Any, Any}, OrderedCollections.OrderedDict{SubString{String}}}

```

Get the remotes of repo `r` as an `OrderedDict` the keys of which are the remote names and the values of which are the remote URL's.  Additional keyword arguments are passed to [`rungit`](@ref).
