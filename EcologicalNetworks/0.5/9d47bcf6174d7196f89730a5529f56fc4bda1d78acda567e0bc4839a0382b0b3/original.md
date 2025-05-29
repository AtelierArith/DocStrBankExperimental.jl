```
Q(N::T, L::Dict{E,Int64}) where {T<:AbstractEcologicalNetwork,E}
```

Modularity of a network and its partition. The second argument is a dictionary where every species of `N` is associated to an `Int64` value representing the identity of the module. This function returns the same value of bipartite networks and their unipartite projection.

#### References

  * Barber, M.J., 2007. Modularity and community detection in bipartite networks. Phys. Rev. E 76, 066102. https://doi.org/10.1103/PhysRevE.76.066102
  * Newman, M.E., 2006. Modularity and community structure in networks. Proceedings of the national academy of sciences 103, 8577–8582.
