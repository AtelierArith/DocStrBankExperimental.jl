```
writepdb(output, element, atom_selectors...)
```

Write a `StructuralElementOrList` to a Protein Data Bank (PDB) format file or output stream.

Only ATOM, HETATM, MODEL and ENDMDL records are written - there is no header and there are no TER records. Atom selector functions can be given as additional arguments - only atoms that return `true` from all the functions are retained. The keyword argument `expand_disordered` (default `true`) determines whether to return all copies of disordered residues and atoms.
