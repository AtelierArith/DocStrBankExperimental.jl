```
betadiversity(::Type{βWN},U::T,V::T) where {T <: SpeciesInteractionNetwork{<:Partiteness, <:Binary}}
```

Network-level β diversity between networks. By default, this return the species dissimilarity for the entire network. An optional last argument `dims` can be used, to specify top (`1`) and bottom (`2`) levels.
