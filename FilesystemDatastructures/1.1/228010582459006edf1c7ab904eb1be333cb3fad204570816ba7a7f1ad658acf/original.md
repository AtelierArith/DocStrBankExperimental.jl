```
add!(scfc::SizeConstrainedFileCache, key::AbstractString, new_size)
```

Reserves space for a new file within the file cache of the specified size.  If the addition would result in a new total size that is greater than the target specified by the `target_size` function passed to the SCFC constructor, `shrink!()` the file cache until this new object can fit nicely within the cache without overstepping any file size bounds.  If the new object cannot fit wihtin the cache at all, throws an `ArgumentError`.

`add!()`'ing an entry that already exists within the file cache overwrites it and clears all access counters, treating it as a semantically different object than the object that was replaced.
