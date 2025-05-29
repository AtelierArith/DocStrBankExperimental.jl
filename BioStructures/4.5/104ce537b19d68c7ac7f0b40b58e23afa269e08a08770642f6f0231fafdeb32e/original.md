```
rmsd(element_one, element_two, residue_selectors...)
rmsd(element_one, element_two, superimpose=false)
rmsd(coords_one, coords_two)
```

Get the root-mean-square deviation (RMSD) in Å between two `StructuralElementOrList`s or two coordinate `Array`s.

If `superimpose` is `true` (the default), the elements are superimposed before RMSD calculation and the RMSD is calculated on the superimposed residues. In this case the BioSequences.jl and BioAlignments.jl packages should be imported. See `Transformation` for keyword arguments. If `superimpose` is `false` the elements are assumed to be superimposed and must be of the same length. The keyword argument `rmsdatoms` is an atom selector that selects the atoms to calculate RMSD on (default `calphaselector`).
