```
RPath
```

This type encapsulates the search path used by an object file when looking for a shared library.  This class enables not only looking at the path, but querying the path for matches for given library names.  The list of available API operations is given below, with methods that subclasses must implement marked in emphasis:

### Creation:

  * *RPath()*

### Utility

  * *handle()*

### RPath operations

  * *rpaths()*
  * canonical_rpaths()
  * find_library()
  * lastindex()
  * iterate()
