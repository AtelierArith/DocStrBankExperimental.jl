```
kekulize(mol::SimpleMolGraph) -> Vector{Int}
```

Return an array of bond orders with kekulization applied.

Double bonds and single bonds will be assigned to aromatic rings which consist of SMILES lowercase atoms (called Kekulization). Kekulization is necessary for the valence and implicit hydrogens of a molecule parsed from SMILES to be correctly evaluated.
