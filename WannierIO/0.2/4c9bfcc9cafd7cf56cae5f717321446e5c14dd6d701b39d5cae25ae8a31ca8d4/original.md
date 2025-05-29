```
write_unk(filename, ik, Ψ; binary=false)
write_unk(filename, ik, Ψ, ::FortranText)
write_unk(filename, ik, Ψ, ::FortranBinary)
```

Write `UNK` file for the periodic part of Bloch wavefunctions.

# Arguments

  * ik: at which kpoint? start from 1
  * Ψ: Bloch wavefunctions, `size(Ψ) = (n_gx, n_gy, n_gz, n_bands, n_spin)`

# Keyword arguments

  * `binary`: write as Fortran unformatted file
