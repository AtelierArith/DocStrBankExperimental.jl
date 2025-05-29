```
setmetadata!(x, value)
```

Set metadata in `x` to `value`, a `Dict` where the keys are the metadata field names.

# Examples

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> setmetadata!(x, Dict{String,Any}("foo" => 200));

julia> metadata(x)
Dict{String, Any} with 1 entry:
  "foo" => 200
```
