```
MachOLoadCmd(oh::MachOHeader, CT::Type{MachORPathCmd}, header)
```

Manual override to unpack a `MachORPathCmd` from a MachO file and immediately read in the associated rpath string.
