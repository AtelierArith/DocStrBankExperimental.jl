```
sampledata(x, check = true)
```

Return a `DataFrame` containing the sample data in the `MultiAssayExperiment` `x`.

The returned object should contain `name` as the first column, containing a vector of unique strings. If `check = true`, the function will check the validity of the sample data before returning it.

# Examples

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> names(sampledata(x))
2-element Vector{String}:
 "name"
 "disease"
```
