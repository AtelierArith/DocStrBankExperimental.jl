```
section_name(section::Section)
```

Return the name of the given section as a string.  In order to return a true name, it is necessary to perform a lookup within the object's string table, which cannot be done using just a `Section` object; use a `SectionRef` object instead if you need that.  For sanity sake, this method will return a string, but the contents of the string may be something like the offset within the string table pointing to this `Section`'s name, e.g. "@strtab.123"
