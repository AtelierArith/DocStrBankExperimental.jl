```
fload_Matrix_Sync(fileLocation,fileName)
```

Loads just the S and T Matricies stored in `fileName` stored at `fileLocation`. 

# Example

```julia-repl
    Matricies = fload_Matrix_Sync(fileLocation,fileName);
```

Returns a tuple of the data stored in the file. The fields are as follows:

  * `SMatrix` : A 4D matrix of the emission spectrum for Synchrotron.
