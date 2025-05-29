```
Segment
```

An abstraction over the concept of a `Segment` within an object file.  A `Segment` is a portion of an object file that is given instruction on its layout in virtual memory; this is in contrast to a `Section`, which delineates different portions of an object file on disk.  ELF files have the strictest separation here, with a single executable file containing multiple `Segment` and `Section` objects, with `Section`s being assigned to one or more `Segment`s for virtual memory placement.  Mach-O files typically have two `Segment`s, one called `__TEXT`, one called `__DATA`.  COFF files do not have `Segment`.

Just like with `Section` objects, many operations upon segments require global operations (access to the string table, knowledge of position within the file, etc...) which causes some operations to be defined only upon the `SegmentRef` datatype.  As a user, the `SegmentRef` type should be the primary method of interacting with segments, as a developer adding new object file formats, some methods must support `Segment`s, others must support only `SegmentRef`s. Note that any method that works on a `Segment` must also work with a `SegmentRef`, see the `@derefmethod` macro for a convenient helper macro to generate `SegmentRef` -> `Section` wrapper methods. The list of available API operations is given below, with methods that subclasses must implement marked in emphasis:

### Creation:

  * *read()*

### Utility:

  * deref()

### Format-specific properties:

  * *segment_name()*
  * *segment_offset()*
  * *segment*file*size()*
  * *segment*memory*size()*
  * *segment_address()*
