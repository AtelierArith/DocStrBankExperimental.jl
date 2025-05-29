```
section_header_type(oh::ObjectHandle)
```

Given an `ObjectHandle`, return the type of a section header (used for reading in the sections header when trying to load a `Section` object or iterating over a `Sections` object).  For instance, for a 64-bit ELF file, this would return the type `ELFSection64`
