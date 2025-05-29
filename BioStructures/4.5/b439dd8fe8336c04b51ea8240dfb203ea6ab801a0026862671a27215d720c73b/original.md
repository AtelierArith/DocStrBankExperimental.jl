```
coordarray(element, atom_selectors...)
```

Get the atomic coordinates in Å of a `StructuralElementOrList` as a 2D `Array`.

Each column corresponds to one atom, so the size is (3, n*atoms). Additional arguments are atom selector functions - only atoms that return `true` from all the functions are retained. The keyword argument `expand*disordered`(default`false`) determines whether to return coordinates for all copies of disordered atoms separately.
