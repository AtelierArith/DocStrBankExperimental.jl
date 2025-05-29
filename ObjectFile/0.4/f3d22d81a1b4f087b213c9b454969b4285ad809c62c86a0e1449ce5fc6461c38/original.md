```
SegmentRef
```

Provides a reference to a `Segment`, along with a reference to the `ObjectHandle` this `Segment` comes from.  This should be the primary method by which users interact with segments inside object files.  The list of available API operations is given below, with methods that subclasses must implement marked in emphasis.  Note that this overlaps heavily with the `Segment` object API, this is by design as many of the methods are simply passthroughs to the underlying `Segment` API calls for ease of use.

### Creation:

  * *SegmentRef()*

### Utility

  * *deref()*
  * *Segments()*
  * handle()

### Format-specific properties:

  * *segment_name()*
  * *segment_number()*
  * segment_offset()
  * segment*file*size()
  * segment*memory*size()
  * segment_address()
