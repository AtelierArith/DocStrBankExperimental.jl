```
stride_run(pdb_file::AbstractString; adjust_pdb=false)
```

Run stride on the PDB file and return a vector containing the `stride` detailed secondary structure information for each residue.

  * `adjust_pdb=true` is used to adjust the format of the PDB file before running `stride`,  which requires a specific header and a specific empty-chain identifier.   In this case, only the ATOM lines are kept in the PDB file.
  * If `adjust_pdb=false`, the PDB file provided is used as is.

Note that `STRIDE` will fail if residue or atoms types not recognized or if the header of the PDB file does not follow the necessary pattern.

!!! note
      * STRIDE might ignore some residues in the PDB file if they are not recognized, or incomplete.
      * STRIDE does not support structures in mmCIF format.

