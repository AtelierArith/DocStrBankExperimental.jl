```
ObjectHandle
```

The basic type that provides access to object files.  The list of available API operations is given below, with methods that subclasses must implement marked in emphasis.  Note tha "must implement" is a bit of a misnomer, if an Object file does not have need of a certain piece of this API (e.g. `COFF` files have no concept of `Segment`s), leaving that chunk of the API undefined will simply cause errors if a user attempts to use methods that use that part of the API (in the example above, an error will be thrown if the user calls `Segments(oh)` where `oh <: COFFHandle`).

### Creation

  * *readmeta()*

### IOStream-like operations:

  * seek()
  * seekstart()
  * skip()
  * startaddr()
  * iostream()
  * position()
  * read()
  * readuntil()
  * eof()
  * unpack()

### Format-specific properties

  * *Platform()*
  * *endianness()*
  * *is64bit()*
  * *isrelocatable()*
  * *isexecutable()*
  * *islibrary()*
  * *isdynamic()*
  * *mangle*section*name()*
  * *mangle*symbol*name()*
  * handle()
  * *header()*
  * *format_string()*

### Section properties

  * *section*header*offset()*
  * *section*header*size()*
  * *section*header*type()*

### Segment properties

  * *segment*header*offset()*
  * *segment*header*size()*
  * *segment*header*type()*

### Symbol properties

  * *symtab*entry*offset()*
  * *symtab*entry*size()*
  * *symtab*entry*type()*

### Misc

  * *path()*
  * show()
  * find_library()
  * find_libraries()
