```
samplemap(x)
```

Return an ordered dictionary containing the sample mapping from the `MultiAssayExperiment` `x`.

The returned object should contain the `sample`, `experiment` and `colname` columns in that order. Each column should contain a vector of strings, and rows should be unique. If `check = true`, the function will check the validity of the sample data before returning it.

# Examples

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> names(samplemap(x))
3-element Vector{String}:
 "sample"
 "experiment"
 "colname"
```
