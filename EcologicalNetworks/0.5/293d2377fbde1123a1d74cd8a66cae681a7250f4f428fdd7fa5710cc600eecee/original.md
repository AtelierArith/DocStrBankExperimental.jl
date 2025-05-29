```
each_species_its_module(N::T) where {T<:AbstractEcologicalNetwork}
```

Returns a dictionary in which each species is its own module. This is used as a starting point for `lp` and `salp` internally. This is often a very poor starting point for `brim`, and should probably not be used on its own.

#### References

Thébault, E., 2013. Identifying compartments in presence–absence matrices and bipartite networks: insights into modularity measures. Journal of Biogeography 40, 759–768. https://doi.org/10.1111/jbi.12015
