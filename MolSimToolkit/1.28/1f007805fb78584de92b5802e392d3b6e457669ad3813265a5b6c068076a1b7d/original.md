```
MDLovoFitResult
```

Data structure to store the output of the `mdlovofit` function.

Fields: 

  * `simulation`: Simulation object with the trajectory of the system and the atom data.
  * `frame_indices`: vector with the frame index of each frame.
  * `rmsd_low`: RMSD of the fraction of the structure with the lowest RMSD.
  * `rmsd_high`: RMSD of the fraction of the structure with the highest RMSD.
  * `rmsd_all`: RMSD of the whole structure.
  * `rmsf`: RMSF as a function of the residue or atom index.
  * `rmsf_file`: name of the file with the RMSF data.
  * `rmsd_file`: name of the file with the RMSD data.
  * `aligned_pdb`: name of the PDB file with the aligned structure.
