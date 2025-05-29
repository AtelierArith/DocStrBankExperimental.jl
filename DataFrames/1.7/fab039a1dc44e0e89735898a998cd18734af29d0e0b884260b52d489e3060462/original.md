```
size(df::AbstractDataFrame[, dim])
```

Return a tuple containing the number of rows and columns of `df`. Optionally a dimension `dim` can be specified, where `1` corresponds to rows and `2` corresponds to columns.

See also: [`nrow`](@ref), [`ncol`](@ref)

# Examples

```jldoctest
julia> df = DataFrame(a=1:3, b='a':'c');

julia> size(df)
(3, 2)

julia> size(df, 1)
3
```
