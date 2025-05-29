```
pdbline(at::Atom)
pdbline(at::DisorderedAtom)
pdbline(at::AtomRecord)
```

Form a Protein Data Bank (PDB) format ATOM or HETATM record as a `String` from an `Atom`, `DisorderedAtom` or `AtomRecord`.

This will throw an `ArgumentError` if a value cannot fit into the allocated space, e.g. the chain ID is longer than one character or the atom serial is greater than 99999. In this case consider using `writemmcif` or `writemmtf` to write a mmCIF file or a MMTF file.
