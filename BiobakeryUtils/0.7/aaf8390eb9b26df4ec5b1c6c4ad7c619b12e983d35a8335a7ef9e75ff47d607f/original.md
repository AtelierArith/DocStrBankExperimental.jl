```
parsetaxon(taxstring::AbstractString, rank::Union{Int, Symbol})
```

Finds given taxonomic rank in a string (as formatted by MetaPhlAn (eg "k**Bacteria|p**Proteobacteria...")) and returns the name and taxonomic rank as a `Taxon`. If taxon rank not given, function will return the most specific (lowest) taxonomic rank available.

Levels may be given either as numbers or symbols:

  * `1` = `:kingdom`
  * `2` = `:phylum`
  * `3` = `:class`
  * `4` = `:order`
  * `5` = `:family`
  * `6` = `:genus`
  * `7` = `:species`
  * `8` = `:subspecies`
