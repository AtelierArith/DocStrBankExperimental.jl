```
to_triple_bond(mol::SimpleMolGraph) -> Nothing
```

Standardize the molecule so that all 1,3-dipole groups are represented as triple bond and single bond (e.g. Diazo group C=[N+]=[N-] -> [C-][N+]#N).
