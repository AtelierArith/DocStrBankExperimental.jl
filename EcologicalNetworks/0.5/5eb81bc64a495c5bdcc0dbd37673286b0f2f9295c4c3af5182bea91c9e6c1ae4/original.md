```
brim(N::NT, L::Dict{E,Int64}) where {NT<:AbstractEcologicalNetwork,E}
```

Uses BRIM to optimize the modularity of an ecological network. The `L` argument is a dictionary mapping every species in the network to its module. This function returns a tuple of the network and its module assignment.

#### References

  * Barber, M.J., 2007. Modularity and community detection in bipartite networks. Phys. Rev. E 76, 066102. https://doi.org/10.1103/PhysRevE.76.066102
  * Newman, M.E., 2006. Modularity and community structure in networks. Proceedings of the national academy of sciences 103, 8577–8582.
  * Thébault, E., 2013. Identifying compartments in presence–absence matrices and bipartite networks: insights into modularity measures. Journal of Biogeography 40, 759–768. https://doi.org/10.1111/jbi.12015
