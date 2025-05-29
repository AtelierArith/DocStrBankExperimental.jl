```
MachODynamicLink
```

MachO type representing a dynamic link between a MachO file and one of its dynamic dependencies.  Although Mach-O encodes more than just the path of the dependency, in order to get at it you will need to dig into the LoadCmd that describes it.
