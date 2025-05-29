```
signatures(G::HermGenus) -> Dict{InfPlc, Int}
```

Given a global genus symbol `G` for hermitian lattices over $E/K$, return the signatures at the infinite places of `K`. For each real place, it is given by the negative index of inertia of the Gram matrix of the rational span of a hermitian lattice whose global genus symbol is `G`.

The output is given as a dictionary with keys the infinite places of `K` and value the corresponding signatures.
