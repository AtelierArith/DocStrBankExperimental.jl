```
refine(collection::DataCollection, datasets::Vector{DataSet}, ident::Identifier)
```

Filter `datasets` (from `collection`) to data sets than match the identifier `ident`.

This function contains an advise entrypoint where plugins can apply further filtering, applied to the method `refine(::Vector{DataSet}, ::Identifier, ::Vector{String})`.
