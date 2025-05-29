```
residuename(residue::Union{AbstractString,Char})
```

Function to return the long residue name from other residue codes. The function is case-insensitive.

### Examples

```julia-repl
julia> residuename("A")
"Alanine"

julia> residuename("Glu")
"Glutamic Acid"

```
