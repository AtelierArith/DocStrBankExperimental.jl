```
remap_to_kstar(
    lgirs::AbstractVector{LGIrrep{D}},
    kv′::KVec{D},
    coset_representatives::AbstractVector{SymOperation{D}}
    ) --> Collection{LGIrrep{D}}
```

Given an set of `LGIrrep`s `lgirs` defined at a **k**-vector `kv`, remap the irrep data to a different **k**-vector `kv′` in the star of `kv`.

The remapping is done by identifying an operation `g` s.t. `kv′ = g * kv` with `g` in the space group of `lgirs` (more precisely, from among the coset representatives of the little group in the space group). The original irreps $D(h)$ with $h$ in the little group of `kv` are then transformed according to $D'(h') = D(h) = D(g⁻¹h'g)$ with $h'$ from the little group of `kv'`.

The coset representatives can be specified as an optional argument, to avoid repeated recomputation and simplify the associated computation of `g`. The coset representatives generate the star of `kv`.
