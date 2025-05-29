```
FileBuffer <: IO
```

A generic buffer type to provide an IO interface for none IO based path types.

NOTES:

  * All `read` operations will read the entire file into the internal buffer at once. Subsequent calls to `read` will only operate on the internal buffer and will not access the filepath.
  * All `write` operations will only write to the internal buffer and `flush`/`close` are required to update the filepath contents.
