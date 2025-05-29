```
collectatoms(el)
```

Returns a `Vector` of the atoms in a `StructuralElementOrList`.

Additional arguments are atom selector functions - only atoms that return `true` from all the functions are retained. The keyword argument `expand_disordered` (default `false`) determines whether to return all copies of disordered atoms separately.
