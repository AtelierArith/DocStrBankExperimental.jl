```
internodecount(N::HybridNetwork; namelist::Union{Nothing,<:AbstractVector{String}}=nothing)
```

Calculates internode counts between all pairs of taxa in network `N`. WARNING: treats `N` as unrooted
