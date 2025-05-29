```
read_struct(oh, type_func, size_func, name)
```

Given a `Type`, (such as `ELFSection64`), `unpack()` it from the given object and return it, throwing errors as appropriate, and skipping over any excess padding bytes as determined by `type_func` and `size_func`. Example invocation:

read*struct(oh, symtab*entry*type, symtab*entry_size, "Symbol Entry")
