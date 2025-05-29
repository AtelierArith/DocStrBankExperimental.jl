```
special(feat::AbstractQuranFeature)
```

Extract the special feature of the token.

# Examples

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> crpsdata = table(crps)
julia> tnzldata = table(tnzl)
julia> special(parse(QuranFeatures, select(crpsdata.data, :features)[53]))
"<in~"
```
