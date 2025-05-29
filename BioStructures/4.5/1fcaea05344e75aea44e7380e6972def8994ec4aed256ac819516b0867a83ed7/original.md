```
countatoms(el)
```

Return the number of atoms in a `StructuralElementOrList` as an `Int`.

Additional arguments are atom selector functions - only atoms that return `true` from all the functions are counted. The keyword argument `expand_disordered` (default `false`) determines whether to return all copies of disordered atoms separately.
