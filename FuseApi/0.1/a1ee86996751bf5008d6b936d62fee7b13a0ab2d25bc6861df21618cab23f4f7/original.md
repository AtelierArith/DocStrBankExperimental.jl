```
FuseFileInfo <: Layout
```

Layout of C-structure used by many fuse callbacks.

The C-structure is allocated and populated by the `libfuse3` C-library and passed as a pointer to the callback functions as an argument `fi::Ptr{FuseFileInfo}`, which is made accessible to Julia by the `CStruct(fi)` conversion.
