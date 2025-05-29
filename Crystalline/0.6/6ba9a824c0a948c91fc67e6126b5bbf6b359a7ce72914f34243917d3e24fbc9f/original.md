```
orbit(g::AbstractVector{<:SymOperation}, kv::KVec, cntr::Char)  -->  Vector{KVec{D}}
orbit(lg::LittleGroup)
orbit(lgir::LGIrrep)
```

Return the orbit of of the reciprocal-space vector `kv` under the action of the group `g`, also known as the star of **k**.

The orbit of `kv` in `g` is the set of inequivalent **k**-points obtained by composition of all the symmetry operations of `g` with `kv`. Two reciprocal vectors $\mathbf{k}$ and $\mathbf{k}'$ are equivalent if they differ by a primitive reciprocal lattice vector.

If `kv` and `g` are specified in a conventional basis but refer to a non-primitive lattice, the centering type `cntr` must be provided to ensure that only equivalence by primitive (not conventional) reciprocal lattice vectors are considered. If the centering type of the group `g` can be inferred from `g` (e.g., if `g` is a `SpaceGroup`), `orbit` will assume a conventional setting and use the inferred centering type; otherwise, if `cntr` is neither explicitly set nor inferrable, a primitive setting is assumed.
