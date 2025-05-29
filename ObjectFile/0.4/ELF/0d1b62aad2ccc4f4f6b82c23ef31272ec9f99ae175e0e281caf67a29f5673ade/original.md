```
ELFDynEntries(oh::ELFHandle, kinds::Vector)
```

Read all `ELFDynEntry` objects from an ELF object, returning them as an array if they are one of the `kinds` passed in, such as `DT_NEEDED`.
