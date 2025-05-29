```
MachOLoadCmd
```

Abstraction over all Load Commands that can exist within a Mach-O object file, containing subclasses such as `MachOSegmentCmd` or `MachODySymtabCmd`. The list of available API operations is given below, with methods that subclasses must implement marked in emphasis:

### Creation

  * MachOLoadCmd()
