```
get(db::Taxonomy.DB, idx::Union{Int,Symbol}, default)
```

Return the Taxon object stored for the given taxid or rank (i.e. :phylum), or the given default value if no mapping for the taxid is present.
