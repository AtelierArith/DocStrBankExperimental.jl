```
rowdata(x; check = true)
```

Return the row annotations as a `DataFrame` with number of rows equal to the number of rows in `x`. The first column is called `"name"` and contains the row names of `x`; this can either be an `AbstractVector{AbstractString}` or a `Vector{Nothing}` (if no row names are available).

If `check = true`, this function will verify that the above expectations on the returned `DataFrame` are satisfied. Any failures will cause warnings to be emitted.

# Examples

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> names(rowdata(x))
2-element Vector{String}:
 "name"
 "Type"

julia> size(rowdata(x))
(20, 2)
```
