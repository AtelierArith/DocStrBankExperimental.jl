```
phiangle(res, res_previous)
phiangle(chain, res_id)
```

Calculate the phi angle in radians for an `AbstractResidue`.

Arguments can either be a residue and the previous residue or a chain and the position as a residue ID. The first residue (or one at the given index) requires the atoms "N", "CA" and "C" and the previous residue requires the atom "C". The angle is in the range -π to π.
