```
read_chk(filename)
read_chk(filename, ::FortranText)
read_chk(filename, ::FortranBinary)
```

Read wannier90 `chk` checkpoint file.

Similar to [`read_amn`](@ref), the 1st version auto detect `chk` file format (binary or text) and read it.
