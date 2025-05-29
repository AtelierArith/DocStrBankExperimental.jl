```
Context(ceed::Ceed, data; mtype=MEM_HOST, cmode=USE_POINTER)
```

Create a `CeedQFunctionContext` object that allows user Q-functions to access an arbitrary data object. `data` should be an instance of a mutable struct. If the copy mode `cmode` is `USE_POINTER`, then the data will be preserved from the GC when assigned to a `QFunction` object using `set_context!`.

Copy mode `OWN_POINTER` is not supported by this interface because Julia-allocated objects cannot be freed from C.
