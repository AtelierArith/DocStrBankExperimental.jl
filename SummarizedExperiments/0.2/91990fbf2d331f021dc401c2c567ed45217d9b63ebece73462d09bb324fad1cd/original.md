```
metadata(x)
```

Return metadata from `x` as a `Dict` where the keys are the metadata field names.

# Examples

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> metadata(x)
Dict{String, Any} with 1 entry:
  "version" => "1.1.0"
```
