```
viewfile(file)
viewfile(file, format)
```

View a molecular structure from a file. Displays in a popup window, or in the output cell for a notebook. Arguments are the filepath and the format ("pdb", "sdf", "xyz" or "mol2"). If not provided, the format is guessed from the file extension, e.g. "myfile.xyz" is treated as being in the xyz format. Optional keyword arguments are `style`, `surface`, `isosurface`, `box`, `lines`, `cylinders`, `vtkcell`, `axes`, `cameraangle`, `height`, `width`, `html` and `debug`.
