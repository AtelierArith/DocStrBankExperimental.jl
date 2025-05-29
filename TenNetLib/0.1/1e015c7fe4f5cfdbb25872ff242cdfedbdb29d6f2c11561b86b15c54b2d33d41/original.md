```
function subspace_expand!(psi::TTN, node::Int2, nextnode::Int2,
                          max_expand_dim::Int, noise::Float64)
```

Enlarges the bond domension between `node` and `nextnode` by `max_expand_dim` using the subspace expansion. The parameter `noise` controls stength of the perturbation.
