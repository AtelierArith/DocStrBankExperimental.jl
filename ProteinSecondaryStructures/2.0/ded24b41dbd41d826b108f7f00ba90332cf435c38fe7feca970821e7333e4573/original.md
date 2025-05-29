```
dssp_run(input_file::String; adjust_pdb=false)
```

Run DSSP on the PDB or mmCIF file provided and return a vector containing the detailed secondary structure information for each residue.

  * `adjust_pdb` option is used to fix the header of PDB files before running `dssp`,   which is a common problem for computing the secondary structure from PDB files.  In this case, only the ATOM lines are kept in the pdb file.
  * `adjust_pdb=false`, the PDB file provided is used as is. This (default) option must be used  when the input file is in mmCIF format.

Note that `DSSP` will fail if residue or atoms types not recognized or if the header of the PDB file does not follow the necessary pattern.
