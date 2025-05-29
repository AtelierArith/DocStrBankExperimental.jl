```
omegaangle(res, res_previous)
omegaangle(chain, res_id)
```

Calculate the omega angle in radians for an `AbstractResidue`.

Arguments can either be a residue and the previous residue or a chain and the position as a residue ID. The first residue (or one at the given index) requires the atoms "N" and "CA" and the previous residue requires the atoms "CA" and "C". The angle is in the range -π to π.
