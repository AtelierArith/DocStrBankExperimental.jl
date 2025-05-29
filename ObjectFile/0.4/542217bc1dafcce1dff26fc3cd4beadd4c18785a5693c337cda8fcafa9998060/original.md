```
StrTab
```

This type encapsulates a string table within an object file, enabling queries against the string table for symbol names, section names, etc... The list of available API operations is given below, with methods that subclasses must implement marked in emphasis:

### Creation

  * *StrTab()*

### Accessors

  * *handle()*
  * *strtab_lookup()*
