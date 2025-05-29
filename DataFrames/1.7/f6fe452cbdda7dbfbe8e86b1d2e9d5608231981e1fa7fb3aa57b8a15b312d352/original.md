```
nrow(df::AbstractDataFrame)
```

Return the number of rows in an `AbstractDataFrame` `df`.

See also: [`ncol`](@ref), [`size`](@ref).

# Examples

```jldoctest
julia> df = DataFrame(i=1:10, x=rand(10), y=rand(["a", "b", "c"], 10));

julia> nrow(df)
10
```
