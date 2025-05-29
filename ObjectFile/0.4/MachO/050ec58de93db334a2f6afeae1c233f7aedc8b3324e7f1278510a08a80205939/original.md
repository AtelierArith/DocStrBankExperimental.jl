```
MachOLoadCmd(oh::MachOHeader, CT::Type{MachOLoadDylibCmd}, header)
MachOLoadCmd(oh::MachOHeader, CT::Type{MachOIdDylibCmd}, header)
```

Manual override to unpack a `MachOLoadDylibCmd` from a MachO file and immediately read in the associated name string.  See `MachODylibStub` for more.
