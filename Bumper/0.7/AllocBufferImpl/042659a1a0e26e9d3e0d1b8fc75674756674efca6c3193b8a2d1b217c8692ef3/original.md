```
AllocBuffer{StorageType}
```

This is a simple bump allocator that could be used to store a fixed amount of memory of type `StorageType`, so long as `::StoreageType` supports `pointer`, and `sizeof`.

Do not manually manipulate the fields of an AllocBuffer that is in use.
