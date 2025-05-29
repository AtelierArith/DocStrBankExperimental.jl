```
Section
```

An abstraction over the concept of a `Section` within an object file.  Because many operations upon sections require global operations (access to the string table, knowledge of position within the file, etc...) some operations are defined only upon the `SectionRef` datatype.  As a user, the `SectionRef` type should be the primary method of interacting with sections, as a developer adding new object file formats, some methods must support `Section`s, others must support only `SectionRef`s.  Note that any method that works on a `Section` must also work with a `SectionRef`, see the `@derefmethod` macro for a convenient helper macro to generate `SectionRef` -> `Section` wrapper methods. The list of available API operations is given below, with methods that subclasses must implement marked in emphasis:

### Creation:

  * *read()*

### Utility:

  * deref()

### IO-like operations:

  * read()

### Format-specific properties:

  * *section_name()*
  * *section_size()*
  * *section_offset()*
  * *section_address()*
