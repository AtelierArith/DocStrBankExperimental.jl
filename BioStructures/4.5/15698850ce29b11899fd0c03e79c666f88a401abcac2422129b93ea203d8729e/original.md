```
psiangle(res, res_next)
psiangle(chain, res_id)
```

Calculate the psi angle in radians for an `AbstractResidue`.

Arguments can either be a residue and the next residue or a chain and the position as a residue ID. The first residue (or one at the given index) requires the atoms "N", "CA" and "C" and the next residue requires the atom "N". The angle is in the range -π to π.
