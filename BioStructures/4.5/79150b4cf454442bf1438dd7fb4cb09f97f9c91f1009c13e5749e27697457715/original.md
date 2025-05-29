```
collectresidues(el)
```

Returns a `Vector` of the residues in a `StructuralElementOrList`.

Additional arguments are residue selector functions - only residues that return `true` from all the functions are retained. The keyword argument `expand_disordered` (default `false`) determines whether to return all copies of disordered residues separately.
