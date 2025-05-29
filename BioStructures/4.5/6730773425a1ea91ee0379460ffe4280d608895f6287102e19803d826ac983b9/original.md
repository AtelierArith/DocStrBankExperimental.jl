```
countresidues(el)
```

Return the number of residues in a `StructuralElementOrList` as an `Int`.

Additional arguments are residue selector functions - only residues that return `true` from all the functions are counted. The keyword argument `expand_disordered` (default `false`) determines whether to return all copies of disordered residues separately.
