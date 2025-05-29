```
size(x::SummarizedExperiment)
```

Return a 2-tuple containing the number of rows and columns in `x`.

# Examples

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> size(x)
(20, 10)
```
