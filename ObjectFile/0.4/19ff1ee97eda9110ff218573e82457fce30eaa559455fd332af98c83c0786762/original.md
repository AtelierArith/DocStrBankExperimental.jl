```
SymbolRef
```

Provides a reference to a `SymtabEntry`, along with a reference to the `ObjectHandle` this `SymtabEntry` comes from.  This should be the primary method by which users interact with symbols inside object files.  The list of available API operations is given below, with methods that subclasses must implement marked in emphasis.  Note that this overlaps heavily with the `SymtabEntry` object API, this is by design as many of the methods are simply passthroughs to the underlying `SymtabEntry` API calls for ease of use.

### Creation:

  * *SymbolRef()*

### Util:

  * *deref()*
  * *Symbols()*
  * handle()

### Properties:

  * *symbol_number()*
  * *symbol_name()*
  * symbol_value()
  * isundef()
