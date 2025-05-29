**Get information about a taxon at any level**

```
taxon(name::String)
```

This function will look for a taxon by its (scientific) name in the GBIF reference taxonomy.

Optional arguments are

  * `rank::Union{Symbol,Nothing}=:SPECIES` – the rank of the taxon you want. This is part of a controlled vocabulary, and can only be one of `:DOMAIN`, `:CLASS`, `:CULTIVAR`, `:FAMILY`, `:FORM`, `:GENUS`, `:INFORMAL`, `:ORDER`, `:PHYLUM,`, `:SECTION`, `:SUBCLASS`, `:VARIETY`, `:TRIBE`, `:KINGDOM`, `:SUBFAMILY`, `:SUBFORM`, `:SUBGENUS`, `:SUBKINGDOM`, `:SUBORDER`, `:SUBPHYLUM`, `:SUBSECTION`, `:SUBSPECIES`, `:SUBTRIBE`, `:SUBVARIETY`, `:SUPERCLASS`, `:SUPERFAMILY`, `:SUPERORDER`, and `:SPECIES`
  * `strict::Bool=true` – whether the match should be strict, or fuzzy

Finally, one can also specify other levels of the taxonomy, using  `kingdom`, `phylum`, `class`, `order`, `family`, and `genus`, all of which can either be `String` or `Nothing`.

If a match is found, the result will be given as a `GBIFTaxon`. If not, this function will return `nothing` and give a warning.
