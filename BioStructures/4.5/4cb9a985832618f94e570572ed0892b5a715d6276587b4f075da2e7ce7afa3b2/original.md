```
writemmcif(output, element, atom_selectors...; gzip=false)
writemmcif(output, mmcif_dict; gzip=false)
```

Write a `StructuralElementOrList` or a `MMCIFDict` to a mmCIF format file or output stream.

Atom selector functions can be given as additional arguments - only atoms that return `true` from all the functions are retained. The keyword argument `expand_disordered` (default `true`) determines whether to return all copies of disordered residues and atoms. The keyword argument `gzip` (default `false`) determines if the output is gzipped.
