```
fload_Matrix_ISO(fileLocation,fileName)
```

Loads just the S and T Matrices stored in `fileName` stored at `fileLocation` first converting them to an isotropic form by summing over angles. (The dimensions of the matrices stay the same i.e. 6D->6D with three dimensions having a size of 1)

# Example

```julia-repl
    Matrices = fload_All_ISO(fileLocation,fileName);
```

Returns a tuple of the data stored in the file. The fields are as follows:

  * `Parameters` : A tuple of the parameters used in the evaluation.
  * `SMatrix3` : A 6D matrix of the emission spectrum for 12->34 interaction.
  * `SMatrix4` : A 6D matrix of the emission spectrum for 12->43 interaction.
  * `TMatrix1` : A 4D matrix of the absorption spectrum for 12->34 interaction.
  * `TMatrix2` : A 4D matrix of the absorption spectrum for 21->34 interaction.

If initial or final particles are identical then only one of the SMatrices or TMatrices will be returned for that state.
