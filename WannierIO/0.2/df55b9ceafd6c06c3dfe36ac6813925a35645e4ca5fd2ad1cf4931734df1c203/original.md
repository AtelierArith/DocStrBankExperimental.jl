```
write_eig(filename, eigenvalues; binary=false)
write_eig(filename, eigenvalues, ::FortranText)
write_eig(filename, eigenvalues, ::FortranBinaryStream)
```

Write `eig` file.

# Arguments

  * `eigenvalues`: a length-`n_kpts` vector, each element is a length-`n_bands` vector

# Keyword arguments

  * `binary`: if true write in Fortran binary format.
