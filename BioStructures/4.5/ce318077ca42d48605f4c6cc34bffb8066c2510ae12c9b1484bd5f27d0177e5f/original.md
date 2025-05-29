```
displacements(element_one, element_two, residue_selectors...)
displacements(element_one, element_two, superimpose=false)
displacements(coords_one, coords_two)
```

Get the displacements in Å between atomic coordinates from two `StructuralElementOrList`s or two coordinate `Array`s.

If `superimpose` is `true` (the default), the elements are superimposed before calculation and the displacements are calculated on the superimposed residues. In this case the BioSequences.jl and BioAlignments.jl packages should be imported. See `Transformation` for keyword arguments. If `superimpose` is `false` the elements are assumed to be superimposed and must be of the same length. The keyword argument `dispatoms` is an atom selector that selects the atoms to calculate displacements on (default `calphaselector`).
