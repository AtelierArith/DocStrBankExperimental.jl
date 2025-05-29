```
sqdistance(element_one, element_two, atom_selectors...)
```

Get the minimum square distance in Å between two `StructuralElementOrList`s.

Additional arguments are atom selector functions - only atoms that return `true` from the functions are retained.
