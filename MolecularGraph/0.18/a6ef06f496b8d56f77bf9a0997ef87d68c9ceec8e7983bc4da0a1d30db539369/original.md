```
is_ring_aromatic(mol::SimpleMolGraph) -> Vector{Bool}
```

Returns a vector of size $n$ representing whether first to $n$-th rings of a given molecule are aromatic or not.

This is a binary descriptor based on a chemoinformatic algorithm and may not reflect actual molecular orbitals. Atypical aromaticities such as Moebius aromaticity are not considered.
