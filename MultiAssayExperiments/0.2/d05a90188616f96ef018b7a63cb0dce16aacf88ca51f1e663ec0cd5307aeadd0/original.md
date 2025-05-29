```
setexperiments!(x, value)
```

Set the experiments in the `MultiAssayExperiment` `x` to the `OrderedDict` `value`. This returns a reference to the modified `x`.

# Examples

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> y = copy(experiments(x));

julia> delete!(y, "foo");

julia> setexperiments!(x, y);

julia> collect(keys(experiments(x)))
1-element Vector{String}:
 "bar"
```
