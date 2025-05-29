```
SymtabEntry
```

An abstraction over the concept of a symbol within an object file.  This type does not use the `Symbol` name as this would conflict with the builtin Julia `Symbol` type, so the name `SymtabEntry` is used instead.  As a user, the `SymbolRef` type should be the primary method of interacting with symbols, as a developer adding new object file formats, some methods must support `SymtabEntry`s, others must support only `SymbolRef`s.  Note that any method that works on a `SymtabEntry` must also work with a `SymbolRef`, see the `@derefmethod` macro for a convenient helper macro to generate `SymbolRef` -> `SymtabEntry` wrapper methods. The list of available API operations is given below, with methods that subclasses must implement marked in emphasis:

### Creation:

  * *SymtabEntry()*

### Util:

  * deref()

### Properties:

  * *symbol_name()*
  * *symbol_value()*
  * *isundef()*
  * *isglobal()*
  * *islocal()*
  * *isweak()*
