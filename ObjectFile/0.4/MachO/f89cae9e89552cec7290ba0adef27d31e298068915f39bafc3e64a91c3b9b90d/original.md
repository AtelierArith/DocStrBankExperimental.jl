```
MachOIdDylibCmd
```

MachO dylibs have an "identity", analogous to the SONAME of an ELF shared library.  This Load Command tells the linker about the identity of this particular shared library.  The API of this object is identical to that of the `MachOLoadDylibCmd` object, as they are intrinsically identical, it is the semantic meaning behind the data that changes, and so this object is all but a typealias for `MachOLoadDylibCmd`.
