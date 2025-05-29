```
write_amn(filename, A; header=default_header(), binary=false)
write_amn(filename, A, ::FortranText; header=default_header())
write_amn(filename, A, ::FortranBinaryStream; header=default_header())
```

Write wannier90 `amn` file.

# Arguments

  * `filename`: output filename
  * `A`: a length-`n_kpts` vector, each element is a `n_bands * n_wann` matrix

# Keyword arguments

  * `header`: 1st line of the file
  * `binary`: write as Fortran unformatted file, which is the Wannier90 default.   Here the `binary` kwargs is provided for convenience.

Same as [`read_amn`](@ref) there are three versions of this function, the 1st one is a wrapper function, it calls the 2nd or the 3rd version depending on the `binary` kwargs.
