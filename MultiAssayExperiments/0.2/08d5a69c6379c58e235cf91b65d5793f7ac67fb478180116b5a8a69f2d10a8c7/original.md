```
setmetadata!(x, value)
```

Set the metadata of a `MultiAssayExperiment` `x` to a dictionary `value`. This returns a reference to the modified `x`.

# Examples

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> meta = copy(metadata(x));

julia> meta["version"] = "0.2.0";

julia> setmetadata!(x, meta);

julia> metadata(x)["version"]
"0.2.0"
```
