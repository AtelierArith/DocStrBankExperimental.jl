```
StrTab(section::SectionRef{ELFHandle})
```

Special short-cut constructor to build an `StrTab` directly from an ELF `Section`, without attempting to automatically discover the correct section for a string table.
