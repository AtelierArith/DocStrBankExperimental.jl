```
metadata(x, key::Symbol)
metadata(x, key::Symbol, idx)
```

Provide implementation-specific metadata for the given buffer or stream. For instance, data from a WAV file might have metadata that comes from extra chunks read from the file. If no `idx` is given then the first piece of metadata matching the key is returned. If there are multiple matches, the user can provide an index, or `:` to return a list of all matching metadata.
