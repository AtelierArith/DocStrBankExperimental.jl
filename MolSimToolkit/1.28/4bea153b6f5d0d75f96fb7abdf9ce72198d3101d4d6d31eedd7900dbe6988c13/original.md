```
MapFractionsResult
```

Data structure to store the output of the `map_fractions` function.

Fields:

  * `simulation` is a Simulation object with the trajectory of the system and the atom data.
  * `frame_indices` contains the frame index of each frame considered.
  * `fraction` contains the fraction of atoms considered in the alignment.
  * `rmsd_low` contains the RMSD of the fraction of the structure with the lowest RMSD.
  * `rmsd_high` contains the RMSD of the fraction not considered for the alignment.
  * `rmsd_all` contains the RMSD of the whole structure.
