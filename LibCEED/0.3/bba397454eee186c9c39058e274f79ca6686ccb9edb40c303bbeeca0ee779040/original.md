```
CopyMode
```

One of `COPY_VALUES`, `USE_POINTER` or `OWN_POINTER`.

`OWN_POINTER` is not typically supported for objects created in Julia, because those must be destroyed by the garbage collector, and cannot be freed from C.
