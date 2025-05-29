```
resname(residue::Union{AbstractString,Char})
```

Returns the residue name, given the one-letter code or residue name. Differently from `threeletter`, this function will return the force-field name if available in the list of protein residues.

# Examples

```julia-repl
julia> resname("ALA")
"ALA"

julia> resname("GLUP")
"GLUP"
```
