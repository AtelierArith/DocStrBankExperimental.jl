```
Sections
```

An abstraction over the concept of a collection of `Section` types within an object file.  One can think of the `Sections` object containing the table of section headers within the object file, whereas the `Section`/`SectionRef` objects contain the actual section data itself.  The list of available API operations is given below, with methods that subclasses must implement marked in emphasis:

### Creation

  * *Sections()*

### Iteration

  * getindex()
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
