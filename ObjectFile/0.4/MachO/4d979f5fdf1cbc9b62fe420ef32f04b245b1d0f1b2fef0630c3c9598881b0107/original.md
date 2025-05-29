```
MachOLoadDylibCmd
```

The Load Command that gives information about a dylib that must be loaded for this Mach-O file to link properly.  The API for this laod command is given as follows:

### Creation:

  * MachOLoadCmd()

### Accessors:

  * dylib_name()
  * dylib_timestamp()
  * dylib_version()
  * dylib_compatibility()
