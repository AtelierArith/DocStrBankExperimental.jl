```
read_eig(filename)
read_eig(filename, ::FortranText)
read_eig(filename, ::FortranBinaryStream)
```

Read the wannier90 `eig` file.

# Return

  * `eigenvalues`: a lenth-`n_kpts` vector, each element is a length-`n_bands` vector

The 1st version is a convenience wrapper function for the 2nd and 3rd versions.
