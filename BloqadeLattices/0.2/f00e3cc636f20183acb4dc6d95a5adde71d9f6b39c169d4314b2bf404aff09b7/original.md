```
generate_sites(lattice::AbstractLattice{D}, repeats::Vararg{Int,D}; scale=1.0)
```

Returns an [`AtomList`](@ref) instance by tiling the specified `lattice`. The tiling repeat the `sites` of the lattice `m` times along the first dimension, `n` times along the second dimension, and so on. `scale` is a real number that re-scales the lattice constant and atom locations.
