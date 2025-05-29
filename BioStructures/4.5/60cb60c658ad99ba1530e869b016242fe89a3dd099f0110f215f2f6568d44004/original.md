```
chiangles(element, residue_selectors...)
```

Calculate the `Vector` of standard χ angles for each residue in a `StructuralElementOrList`. This returns a `Vector` of `Vector`s, where all angles are in the range -π to π. Additional arguments are residue selector functions - only residues that return `true` from the functions are retained.
