```
writemmtf(output, element, atom_selectors...; gzip=false)
writemmtf(output, mmtf_dict; gzip=false)
```

Write a `StructuralElementOrList` or a `MMTFDict` to a MMTF file or output stream.

Requires the MMTF.jl package to be imported. Atom selector functions can be given as additional arguments - only atoms that return `true` from all the functions are retained. The keyword argument `expand_disordered` (default `true`) determines whether to return all copies of disordered residues and atoms. The keyword argument `gzip` (default `false`) determines if the file should be gzipped.
