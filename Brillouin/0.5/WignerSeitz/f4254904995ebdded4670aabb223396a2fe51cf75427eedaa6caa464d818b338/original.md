```
reduce_to_wignerseitz(v::StaticVector, Vs::BasisLike)  -->  v′
```

Return the periodic image `v′` of the point `v` in the basis `Vs`.

`v` is assumed to be provided in the lattice basis (i.e., relative to `Vs`) and `v′` is returned in similar fashion.

The returned point `v′` lies in the Wigner-Seitz cell (or its boundary) defined by `Vs`, has the least possible norm among all equivalent images of `v`, and differs from `v` at most by integer lattice translations such that `mod(v, 1) ≈ mod(v′, 1)`.
