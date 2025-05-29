```
spaceatomname(at::Atom)
```

Space an `Atom` name such that the last element letter (generally) appears in the second column.

If the `element` property of the `Atom` is set it is used to get the element, otherwise the name starts from the second column where possible. This function is generally not required as spacing is recorded when atom names are read in from a Protein Data Bank (PDB) file. However this spacing can be important, for example distinguising between Cα and calcium atoms.
