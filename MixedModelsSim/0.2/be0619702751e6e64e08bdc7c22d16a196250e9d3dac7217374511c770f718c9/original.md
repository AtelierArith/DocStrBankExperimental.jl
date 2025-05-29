```
nlevels(nlev, tag='S')
```

Return a `Vector{String}` of `tag` followed by `1:nlev` left-padded with zeros

# Examples

```julia-repl
julia> show(nlevels(10))
["S01", "S02", "S03", "S04", "S05", "S06", "S07", "S08", "S09", "S10"]
```
