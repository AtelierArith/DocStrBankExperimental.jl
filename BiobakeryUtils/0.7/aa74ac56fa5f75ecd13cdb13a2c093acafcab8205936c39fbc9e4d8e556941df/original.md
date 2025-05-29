```
parsetaxa(taxstring::AbstractString; throw_error=true)
```

Given a string representing taxonmic ranks as formatted by MetaPhlAn (eg "k**Bacteria|p**Proteobacteria..."), separates taxonomic ranks into elements of type Taxon in a vector.
