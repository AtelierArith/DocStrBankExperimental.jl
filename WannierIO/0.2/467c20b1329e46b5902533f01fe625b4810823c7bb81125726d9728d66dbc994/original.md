```
write_chk(filename, chk::Chk; binary=false)
write_chk(filename, chk::Chk, ::FortranText)
write_chk(filename, chk::Chk, ::FortranBinary)
```

Write wannier90 `chk` file.

Similar to [`write_amn`](@ref), the 1st version is a convenience wrapper.

# Keyword arguments

  * `binary`: write as Fortran binary file or not. Although wannier90 default   is Fortran binary format, here the default is `false` since Fortran binary   depends on compiler and platform, so it is not guaranteed to always work.
