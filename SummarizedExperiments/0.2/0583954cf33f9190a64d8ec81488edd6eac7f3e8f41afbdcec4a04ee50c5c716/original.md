```
assays(x; check = true)
```

Return all assays from `x` as an `OrderedDict` where the keys are the assay names. Each returned assay should have the same extents as `x` for the first two dimensions. If `check = true`, this function will verify that this expectation is satisfied. Any failures will cause warnings to be emitted.

# Examples

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> collect(keys(assays(x)))
3-element Vector{String}:
 "foo"
 "bar"
 "whee"
```
