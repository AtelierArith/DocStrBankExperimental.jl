```
mangle_section_name(oh::ObjectHandle, name::AbstractString)
```

Turn a section `name` into the object-format specific naming convention, e.g. returning `".bss"` for `ELF`/`COFF` files, and `"__bss"` for `MachO` files
