```
oneletter(residue::Union{AbstractString,Char})
```

Function to return a one-letter residue code from the three letter code or residue name. The function is case-insensitive.

### Examples

```julia-repl
julia> oneletter("ALA")
"A"

julia> oneletter("Glutamic acid")
"E"

```
