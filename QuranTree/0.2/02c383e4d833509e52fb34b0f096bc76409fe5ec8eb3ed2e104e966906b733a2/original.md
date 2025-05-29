```
root(feat::AbstractQuranFeature)
```

Extract the root of the feature.

# Examples

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> crpsdata = table(crps)
julia> tnzldata = table(tnzl)
julia> root(parse(QuranFeatures, select(crpsdata[112].data, :features)[1]))
"qwl"
```
