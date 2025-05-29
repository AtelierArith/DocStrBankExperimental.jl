```
experiments(x)
```

Return an ordered dictionary containing all experiments in the `MultiAssayExperiment` `x`.

# Examples

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> collect(keys(experiments(x)))
2-element Vector{String}:
 "foo"
 "bar"
```
