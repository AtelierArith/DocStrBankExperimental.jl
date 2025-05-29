```
load_system([parser], file::AbstractString; kwargs...)
load_system([parser], file::AbstractString, index; kwargs...)
```

Read an AtomsBase-compatible system from `file`. If `file` contains more than one structure the last entry is returned. If `index` is specified this indexes into the list of structures and returns the respective system.

By default `AtomsIO` picks an appropriate parser for the specified file format automatically. A specific parser (such as [`AtomsIO.ExtxyzParser`](@ref) or [`AtomsIO.ChemfilesParser`](@ref)) can be enforced by using it as the first argument. Some parsers support additional keyword arguments. E.g. `AseParser` supports the `format` argument to overwrite the ASE-internal selection of an input / output format.
