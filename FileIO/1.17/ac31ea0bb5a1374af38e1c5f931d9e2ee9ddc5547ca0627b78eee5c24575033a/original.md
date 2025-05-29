```
add_format(fmt, magic, extension)
```

registers a new [`DataFormat`](@ref).

For example:

```julia
add_format(format"TIFF", (UInt8[0x4d,0x4d,0x00,0x2b], UInt8[0x49,0x49,0x2a,0x00]), [".tiff", ".tif"])
add_format(format"PNG", [0x89,0x50,0x4e,0x47,0x0d,0x0a,0x1a,0x0a], ".png")
add_format(format"NRRD", "NRRD", [".nrrd",".nhdr"])
```

Note that extensions, magic numbers, and format-identifiers are case-sensitive.

You can also specify particular packages that support the format with `add_format(fmt, magic, extension, pkgspecifiers...)`, where example `pkgspecifiers` are:

```julia
add_format(fmt, magic, extension, [:PkgA=>UUID(...)])                     # only PkgA supports the format (load & save)
add_format(fmt, magic, extension, [:PkgA=>uuidA], [:PkgB=>uuidB])         # try PkgA first, but if it fails try PkgB
add_format(fmt, magic, extension, [:PkgA=>uuidA, LOAD], [:PkgB=>uuidB])   # try PkgA first for `load`, otherwise use PkgB
add_format(fmt, magic, extension, [:PkgA=>uuidA, OSX], [:PkgB=>uuidB])    # use PkgA on OSX, and PkgB otherwise
```

The `uuid`s are all of type `UUID` and can be obtained from the package's `Project.toml` file.

You can combine `LOAD`, `SAVE`, `OSX`, `Unix`, `Windows` and `Linux` arbitrarily to narrow `pkgspecifiers`.
