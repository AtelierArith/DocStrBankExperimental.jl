```
dyn_entry_is_string(d::ELFDynEntry)
```

Return `true` if the given `ELFDynEntry` represents an offset within the dynamic string table, and therefore can be used in a `strtab_lookup()`
