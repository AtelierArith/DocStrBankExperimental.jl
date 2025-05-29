```
COFFSymbols
```

COFF symbol table, contains the list of symbols defined within the object file.

Note that because COFF Symbols are variable-length, we store a table of offsets at which the (non-auxilliary) symbols can be found.
