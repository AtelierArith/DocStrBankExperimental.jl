```
omegaangles(element, residue_selectors...)
```

Calculate the `Vector` of omega angles of a `StructuralElementOrList`.

The vectors have `NaN` for residues where an angle cannot be calculated, e.g. due to missing atoms or lack of an adjacent residue. The angle is in the range -π to π. Additional arguments are residue selector functions - only residues that return `true` from the functions are retained.
