```
Symbols
```

An abstraction over the concept of a collection of symbol (`SymtabEntry`) types within an object file.  One can think of the `Symbols` object containing the table of symbols within the object file, whereas the `SymtabEntry`/`SymbolRef` objects contain the actual symbol data itself.  The list of available API operations is given below, with methods that subclasses must implement marked in emphasis:

### Creation

  * *Symbols()*

### Iteration

  * getindex()
  * *lastindex()*
  * length()
  * iterate()
  * eltype()

### Search

  * findall()
  * findfirst()

### Misc.

  * *handle()*
