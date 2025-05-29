```
SectionRef
```

Provides a reference to a `Section`, along with a reference to the `ObjectHandle` this `Section` comes from.  This should be the primary method by which users interact with sections inside object files.  The list of available API operations is given below, with methods that subclasses must implement marked in emphasis.  Note that this overlaps heavily with the `Section` object API, this is by design as many of the methods are simply passthroughs to the underlying `Section` API calls for ease of use.

### Creation:

  * *SectionRef()*

### Utility

  * *deref()*
  * *handle()*
  * *Sections()*

### IO-like operations:

  * read()
  * seekstart()
  * seek()
  * eof()

### Format-specific properties:

  * section_name()
  * *section_number()*
  * section_type()
  * section_size()
  * section_offset()
  * section_address()
