```
directbasis(sgnum, D=3;    abclims, αβγlims)
directbasis(sgnum, Val(D); abclims, αβγlims) --> DirectBasis{D}
```

Return a random (conventional) `DirectBasis` for a crystal compatible with the space group number `sgnum` and dimensionality `D`. Free parameters in the lattice vectors are chosen randomly, with limits optionally supplied in `abclims` (lengths) and `αβγlims` (angles). By convention, the length of the first lattice vector (`a`) is set to unity, such that the second and third (`b` and `c`) lattice vectors' lengths are relative to the first.

Limits on the relative uniform distribution of lengths `b` and `c` can be specified as  2-tuple kwarg `abclims`; similarly, limits on the angles `α`, `β`, `γ` can be set via αβγlims (only affects oblique, monoclinic, & triclinic lattices).
