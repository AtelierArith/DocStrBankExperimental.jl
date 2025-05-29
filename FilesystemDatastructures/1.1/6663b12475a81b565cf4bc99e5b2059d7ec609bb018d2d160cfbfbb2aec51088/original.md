```
delete!(fc::FileCache, key)
```

Removes a key from the file cache, clearing all metadata about that key within the cache. Also removes the backing file on disk if it still exists.  Returns `true` if the key was actually deleted.
