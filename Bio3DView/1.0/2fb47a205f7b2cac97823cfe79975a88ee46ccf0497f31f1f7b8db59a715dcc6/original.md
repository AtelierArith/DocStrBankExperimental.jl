```
viewstruc(struc)
viewstruc(struc, atom_selectors...)
```

View a structural element from BioStructures.jl. Displays in a popup window, or in the output cell for a notebook. Arguments are a `StructuralElementOrList` and zero or more functions to act as atom selectors - see BioStructures.jl documentation for more. Optional keyword arguments are `style`, `surface`, `isosurface`, `box`, `lines`, `cylinders`, `vtkcell`, `axes`, `cameraangle`, `height`, `width`, `html` and `debug`.
