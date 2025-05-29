```
ramachandranangles(element, residue_selectors...)
```

Calculate the `Vector`s of phi and psi angles of a `StructuralElementOrList`.

The vectors have `NaN` for residues where an angle cannot be calculated, e.g. due to missing atoms or lack of an adjacent residue. The angles are in the range -π to π. Additional arguments are residue selector functions - only residues that return `true` from the functions are retained.
