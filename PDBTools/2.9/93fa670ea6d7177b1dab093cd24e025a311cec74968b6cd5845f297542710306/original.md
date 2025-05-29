```
threeletter(residue::String)
```

Function to return the three-letter natural-amino acid residue code from the one-letter  code or residue name. The function is case-insensitive.

# Examples

```julia-repl
julia> threeletter("A")
"ALA"

julia> threeletter("Aspartic acid")
"ASP"

julia> threeletter("HSD")
"HIS"
```
