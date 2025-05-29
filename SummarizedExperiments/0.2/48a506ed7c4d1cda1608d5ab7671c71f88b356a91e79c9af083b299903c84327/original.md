```
assay(x[, i]; check = true)
```

Return the requested assay in `x`. `i` may be an integer specifying an index or a string containing the name. If `i` is not supplied, the first assay is returned. 

The returned assay should have the same extents as `x` for the first two dimensions. If `check = true`, this function will verify that this expectation is satisfied. Any failures will cause warnings to be emitted.

# Examples

```jldoclist
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

# All of these give the same value.
julia> assay(x);

julia> assay(x, 1);

julia> assay(x, "foo");
```
