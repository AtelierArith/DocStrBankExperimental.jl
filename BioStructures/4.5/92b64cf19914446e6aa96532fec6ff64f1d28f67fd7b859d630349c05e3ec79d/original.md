```
Transformation(el1, el2, residue_selectors...)
Transformation(coords1, coords2)
Transformation(trans1, trans2, rot)
```

A 3D transformation to map one set of coordinates onto another, found using the Kabsch algorithm.

When called with structural elements, carries out a pairwise alignment and superimposes on atoms from aligned residues. In this case the BioSequences.jl and BioAlignments.jl packages should be imported. Keyword arguments for pairwise alignment can be given, see `pairalign`. The residue selectors determine which residues to do the pairwise alignment on. The keyword argument `alignatoms` is an atom selector that selects the atoms to calculate the superimposition on (default `calphaselector`). Can also be called with two sets of coordinates of the same size, with the number of dimensions in the first axis and the number of points in the second axis.

The returned `Transformation` object consists of the mean coordinates of the first set, the mean coordinates of the second set, the rotation to map the first centred set onto the second centred set, and the indices of the aligned residues in the first and second elements if relevant.
