```
primitive_cell(cryst)
```

The shape of a primitive cell in multiples of the lattice vectors for `cryst`. Specifically, columns of `cryst.latvecs * primitive(cryst)` define the primitive lattice vectors in global Cartesian coordinates. Returns `nothing` if spacegroup setting information is missing.

This function may be useful for constructing inputs to [`reshape_supercell`](@ref).
