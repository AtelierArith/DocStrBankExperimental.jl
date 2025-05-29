```
coldata(x, check = true)
```

Return the column annotations as a `DataFrame` with number of rows equal to the number of columns in `x`. The first column is called `"name"` and contains the column names of `x`; this can either be a `Vector{String}` or a `Vector{Nothing}` (if no column names are available).

If `check = true`, this function will verify that the expectations on the returned `DataFrame` are satisfied. Any failures will cause warnings to be emitted.

# Examples

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> names(coldata(x))
3-element Vector{String}:
 "name"
 "Treatment"
 "Response"

julia> size(coldata(x))
(10, 3)
```
