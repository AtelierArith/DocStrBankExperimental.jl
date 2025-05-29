```
read_amn(filename)
read_amn(filename, ::FortranText)
read_amn(filename, ::FortranBinaryStream)
```

Read wannier90 `amn` file.

# Return

  * `A`: length-`n_kpts` vector, each element is a `n_bands * n_wann` matrix.
  * `header`: first line of the file

Note there are three versions of this function: the 1st one is a wrapper function that automatically detect the format (text or binary) of the file, and does some additional pretty printing to give user a quick hint of the dimensions of the A matrix; it internally calls the 2nd or the 3rd version for actual reading.

Wannier90 only has Fortran text format for `amn`, however I wrote a custom version of QE pw2wannier90.x that can output Fortran binary format (using Fortran stream IO) to save some disk space. The 1st function auto detect the file format so it is transparent to the user.
