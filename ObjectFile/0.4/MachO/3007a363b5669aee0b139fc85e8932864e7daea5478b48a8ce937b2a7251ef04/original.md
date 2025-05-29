```
MachOSections
```

Mach-O `Section` object collection type.  Mach-O sections are split out over multiple segments, one per load command.  As an example, most executables have at least two segments, `__DATA` and `__TEXT`, each of which have multiple sections embedded within them.  A `MachOSections` object is created from multiple segments (in this case, realized as multiple load commands) which contain the necessary sections, and these sections can then be accessed as desired.
