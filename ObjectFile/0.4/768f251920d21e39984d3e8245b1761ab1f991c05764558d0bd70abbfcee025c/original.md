```
Segments
```

An abstraction over the concept of a collection of `Segment` types within an object file.  One can think of the `Segments` object containing the table of segment headers within the object file, whereas the `Segment`/`SegmentRef` objects contain the actual segment data itself.  The list of available API operations is given below, with methods that subclasses must implement marked in emphasis:

### Creation

  * *Segments()*

### Iteration

  * *getindex()*
  * *lastindex()*
  * length()
  * iterate()
  * keys()
  * eltype()

### Search

  * findall()
  * findfirst()

### Misc.

  * *handle()*
