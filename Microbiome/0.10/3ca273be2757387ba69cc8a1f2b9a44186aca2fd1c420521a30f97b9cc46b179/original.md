```
Taxon(name::String, rank::Union{Missing, Symbol, Int}) <: AbstractFeature
Taxon(name::String)
```

Microbial taxon with a name and a rank that can be one of 

0. `:domain`
1. `:kingom`
2. `:phylum`
3. `:class`
4. `:order`
5. `:faamily`
6. `:genus`
7. `:species`
8. `:subspecies`
9. `:strain`

or `missing`. Contructors can also use numbers 0-9, or pass a string alone (in which case the `taxon` will be stored as `missing`).

See also [`taxon`](@ref Microbiome.taxon).
