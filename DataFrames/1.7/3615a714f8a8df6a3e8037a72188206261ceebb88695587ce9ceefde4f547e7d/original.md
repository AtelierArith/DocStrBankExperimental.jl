```
ncol(df::AbstractDataFrame)
```

Return the number of columns in an `AbstractDataFrame` `df`.

See also [`nrow`](@ref), [`size`](@ref).

# Examples

```jldoctest
julia> df = DataFrame(i=1:10, x=rand(10), y=rand(["a", "b", "c"], 10));

julia> ncol(df)
3
```
