```
setassays!(x, value)
```

Set assays in `x` to `value`, an `OrderedDict` where the keys are assay names and the values are arrays. All arrays in `value` should have the same extents as `x` for the first two dimensions.

# Examples

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> length(assays(x))
3

julia> refresh = copy(assays(x));

julia> delete!(refresh, "foo");

julia> setassays!(x, refresh)

julia> length(assays(x))
2
```
