```
read_spn(filename)
read_spn(filename, ::FortranText)
read_spn(filename, ::FortranBinary)
```

Read the wannier90 `spn` file.

# Return

  * `Sx`: spin x, a length-`n_kpts` vector, each element is a `n_bands`-by-`n_bands` matrix
  * `Sy`: spin y, a length-`n_kpts` vector, each element is a `n_bands`-by-`n_bands` matrix
  * `Sz`: spin z, a length-`n_kpts` vector, each element is a `n_bands`-by-`n_bands` matrix
  * `header`: 1st line of the file
