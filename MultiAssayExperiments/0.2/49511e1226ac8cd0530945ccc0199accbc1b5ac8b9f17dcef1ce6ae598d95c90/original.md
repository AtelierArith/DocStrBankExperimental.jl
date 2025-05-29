```
metadata(x)
```

Return a dictionary containing the metadata from the `MultiAssayExperiment` `x`.

# Examples

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> collect(keys(metadata(x)))
1-element Vector{String}:
 "version"
```
