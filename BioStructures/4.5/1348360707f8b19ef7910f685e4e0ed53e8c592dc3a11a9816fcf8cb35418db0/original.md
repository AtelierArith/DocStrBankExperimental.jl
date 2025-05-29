```
dihedralangle(atom_a, atom_b, atom_c, atom_d)
dihedralangle(vec_ab, vec_bc, vec_cd)
```

Calculate the dihedral angle in radians defined by four `AbstractAtom`s or three vectors.

The angle between the planes defined by atoms (A, B, C) and (B, C, D) is returned in the range -π to π.
