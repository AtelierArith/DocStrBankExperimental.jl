```
LglPtr
```

Wrapper for the Lingeling solver. The object is fully managed by the Lingeling C library but the memory needs to be released manually using `lgl_release`.

# Fields

  * `ptr::Ptr{Cvoid}`: The pointer to the Lingeling solver.
