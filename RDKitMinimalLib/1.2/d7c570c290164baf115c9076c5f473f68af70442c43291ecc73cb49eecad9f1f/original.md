```
get_svg(mol::Mol, smatches::Vector, details::Dict=Dict{String,Any}())::String
```

Get a SVG depiction of the mol with multiple substructre matches.

```julia
svg = get_svg(mol, get_substruct_matches(mol, query))
```
