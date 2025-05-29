```
function entropy(psi::MPS; kwargs...)
```

Compute von Neumann Entropies of a given MPS `psi` at all the bonds.

Optionally, for specific bonds, keyword argument `bonds` can be specified, e.g., `bonds = [1, 2, 3]`.
