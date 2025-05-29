```
mangle_symbol_name(oh::ObjectHandle, name::AbstractString)
```

Mangle a symbol name using the object-format specific naming convention, e.g. prefixing `"_"` for MachO files.
