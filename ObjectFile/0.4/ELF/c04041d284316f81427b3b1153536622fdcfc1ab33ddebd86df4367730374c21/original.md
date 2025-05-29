```
ELFDynEntry
```

ELF Dynamic table entry type.  This is comprised by a `d_tag` member and a `d_val` member; the `d_tag` tells what kind of command this is to the dynamic linker (e.g. `DT_NEEDED` denotes a shared library that must be loaded for this ELF object to link properly), whereas `d_val` is a pointer to another data structure that contains more information.  (E.g. for a `DT_NEEDED` entry, `d_val` would represent an offset within the dynamic string table)
