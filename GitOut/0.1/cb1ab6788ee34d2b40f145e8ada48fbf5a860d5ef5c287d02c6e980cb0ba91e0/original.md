```julia
init(
    dir::AbstractString;
    template,
    initial_branch,
    bare,
    shared,
    object_format,
    kw...
) -> GitOut.Repo

```

Initialize directory `dir` as a new git repo, see `man git init`. Additional keyword arguments are passed to [`rungit`](@ref).
