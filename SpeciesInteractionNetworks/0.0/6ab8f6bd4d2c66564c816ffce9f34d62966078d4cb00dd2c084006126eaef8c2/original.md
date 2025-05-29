```
betadiversity(::Type{βS},U::T,V::T,dims::Integer = 0,) where {T <: SpeciesInteractionNetwork{<:Partiteness, <:Binary}}
```

Species-level β diversity between networks. By default, this return the species dissimilarity for the entire network. An optional last argument `dims` can be used, to specify top (`1`) and bottom (`2`) levels.
