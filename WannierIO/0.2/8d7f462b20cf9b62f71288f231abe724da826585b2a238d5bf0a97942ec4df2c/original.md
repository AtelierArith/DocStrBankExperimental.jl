```
read_uIu(filename)
read_uIu(filename, ::FortranText; transpose_band_indices=true)
read_uIu(filename, ::FortranBinary; transpose_band_indices=true)
```

Read the wannier90 `uIu` file.

# Keyword Arguments

  * `transpose_band_indices`: QE pw2wannier90.x writes the matrix in a strange   transposed manner; if reading a QE-generated `uIu` file, this flag should   be true to restore the band indices order, so that the returned matrix   has the correct order, i.e.,   `uIu[ik][ib1, ib2][m, n]` is   $\langle u_{m, k + b_1} | u_{n, k + b_2} \rangle$

# Return

  * `uIu`: a length-`n_kpts` vector, each element is a `n_bvecs * n_bvecs` matrix,   then each element is a `n_bands * n_bands` matrix
  * `header`: 1st line of the file
