```julia
status(
    r::GitOut.Repo;
    ...
) -> Base.Generator{Base.EachLine{Base.GenericIOBuffer{SubArray{UInt8, 1, Vector{UInt8}, Tuple{UnitRange{Int64}}, true}}}, typeof(split)}
status(
    r::GitOut.Repo,
    pathspec::Union{Nothing, AbstractString};
    short,
    kw...
) -> Base.Generator{Base.EachLine{Base.GenericIOBuffer{SubArray{UInt8, 1, Vector{UInt8}, Tuple{UnitRange{Int64}}, true}}}, typeof(split)}

```

Returns the status of the git repo `r` as an array the elements of which are the lines of `git status -s`. Additional keyword arguments are passed to [`rungit`](@ref).
