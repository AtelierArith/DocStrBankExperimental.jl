```
print_lineage(lineage::Lineage; kwargs...)
print_lineage(io::IO, lineage::Lineage; kwargs...)
```

Print a formatted representation of the lineage to the given `IO` object.

# Arguments

  * `delim::AbstractString = ";"` - The delimiter between taxon fields.
  * `fill::Bool = false` - If `true`, prints `UnclassifiedTaxon`. only availavle when skip is false.
  * `skip::Bool = false` - If `true`, skip printing `UnclassifiedTaxon` and delimiter.
