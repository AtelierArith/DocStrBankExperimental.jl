```
MachOLoadCmd(oh::MachOHandle, CT::Type, header)
```

Construct a `MachOLoadCmd` from the given `MachOHandle`, constructing an object of type `CT` (which can be calculated via `load_cmd_type(header)`, but is explicitly passed to `MachOLoadCmd()` for dispatch purposes).
