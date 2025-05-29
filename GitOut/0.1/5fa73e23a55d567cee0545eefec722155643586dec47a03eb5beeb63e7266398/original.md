```julia
rungit(r::GitOut.Repo; ...) -> SubString{String}
rungit(r::GitOut.Repo, args; kw...) -> Any

```

Run a git command for the repo `r`.  Additional keyword arguments are passed to [`rungit`](@ref).
