```
setexperiment!(x[, i], value)
```

Set experiment `i` in `MultiAssayExperiment` `x` to the `SummarizedExperiment` `value`. This returns a reference to the modified `x`.

`i` may be a positive integer, in which case it should be no greater than the length of `experiments(x)`. It may also be a string specifying a new or existing experiment in `x`. If omitted, we set the first experiment by default.

# Examples

```jldoctest
julia> using MultiAssayExperiments;

julia> x = MultiAssayExperiments.exampleobject();

julia> size(experiment(x, 2))
(50, 8)

julia> val = experiment(x);

julia> setexperiment!(x, 2, val);

julia> size(experiment(x, 2))
(100, 10)
```
