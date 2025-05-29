```
makecrys(filename::String)
```

Read filename, return crystal object. File can be POSCAR, or simple quantum espresso inputfile

The entire file can be in the string instead of the filename. The code decides which is which by looking for newlines"
