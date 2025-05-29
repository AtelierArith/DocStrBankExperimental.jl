```
add_position_restraints(sys, k; atom_selector=is_any_atom, restrain_coords=sys.coords)
```

Return a copy of a [`System`](@ref) with [`HarmonicPositionRestraint`](@ref)s added to restrain the atoms.

The force constant `k` can be a single value or an array of equal length to the number of atoms in the system. The `atom_selector` function takes in each atom and atom data and determines whether to restrain that atom. For example, [`is_heavy_atom`](@ref) means non-hydrogen atoms are restrained.
