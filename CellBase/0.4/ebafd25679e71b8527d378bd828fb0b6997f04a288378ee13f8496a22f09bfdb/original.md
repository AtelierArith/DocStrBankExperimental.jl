```
write_res(io::IO, structure::Cell)
```

Write out SHELX format data including additional information stored in  `structure.metadata`.

Supported keys: `:label`, `:pressure`, `:volume`, `:enthalpy`, `:spin`, `:abs_spin`, `:symm`, `:flag1`, `flag2`, `flag3`.

The following fields are also treated as the `REM` line:

  * `info`: If a `Dict` is supplied the key-value pairs will be written.
  * `comments`:  Any additional comments to be written. Must be supplied as a `Vector{<:AbstractString}`.

The composition of the structure will be written as `REM Composition: <E1> <N1> <E2> <N2>`.
