```
segment_header_type(oh::ObjectHandle)
```

Given an `ObjectHandle`, return the type of a segment header (used for reading in the segments header when trying to load a `Segment` object or iterating over a `Segments` object).  For instance, for a 64-bit ELF file, this would return the type `ELFSegment64`
