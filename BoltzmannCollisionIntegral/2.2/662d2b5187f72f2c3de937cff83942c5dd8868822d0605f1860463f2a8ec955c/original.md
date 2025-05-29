```
fload_Matrix_SyncISO(fileLocation,fileName)
```

Loads just the S and T Matricies stored in `fileName` stored at `fileLocation` first converting them to an isotropic form by summing over angles. (The dimensions of the matricies stay the same i.e. 6D->6D with three dimensions having a size of 1)

# Example

```julia-repl
    Matricies = fload_Matrix_SyncISO(fileLocation,fileName);
```

Returns a tuple of the data stored in the file. The fields are as follows:

  * `SMatrix` : A 4D matrix of the emission spectrum for Synchrotron.
