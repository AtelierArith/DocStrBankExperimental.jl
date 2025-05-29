```
add!(fc::NFileCache, key::AbstractString, new_size=0)
```

Reserves space for a new file within the file cache. If the number of files exceed the maximum number of entries allowed in the cache the cache delete a file as governed by the discard ordering.
