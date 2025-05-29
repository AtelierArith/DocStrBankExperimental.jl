```
taxon(::AbstractString)
```

Return a [`Taxon`](@ref) from a string representation. If the string contains taxonomic rank information in the form `"x__Thename"` where `x` is the first letter of the rank, this information will be used.

## Examples

```julia-repl
julia> taxon("Unknown")
Taxon("Unknown", missing)

julia> taxon("s__Prevotella_copri")
Taxon("Prevotella_copri", :species)
```
