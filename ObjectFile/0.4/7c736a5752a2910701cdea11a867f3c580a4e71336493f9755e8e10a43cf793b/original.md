```
symtab_entry_type(oh::ObjectHandle)
```

Given an `ObjectHandle`, return the type of a symbol table entry (used for reading in the symbol table when trying to load a `SymtabEntry` object or iterating over a `Symbols` object).  For instance, for a 64-bit ELF file, this would return the type `ELFSymtabEntry64`
