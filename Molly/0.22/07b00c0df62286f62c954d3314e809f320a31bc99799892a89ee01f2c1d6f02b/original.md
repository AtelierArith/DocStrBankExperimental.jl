```
rmsd(coords_1, coords_2)
```

Calculate the root-mean-square deviation (RMSD) of two sets of 3D coordinates after superimposition by the Kabsch algorithm.

Assumes the coordinates do not cross the bounding box, i.e. all coordinates in each set correspond to the same periodic image.
