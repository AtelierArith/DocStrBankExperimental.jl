```
NFileCache <: FileCache
```

Represents a number-of-files-constrained file cache. Configurable with maximum number of files in the cache and how to choose which elements to discard.

```
NFileCache(root, nfiles, discard_func; predicate=x->true)
```

Construct a new file cache. Arguments:

  * `root`: the root directory of the cache.
  * `nfiles`: number of files to retain.
  * `discard_func`: function that return the eviction order, see e.g. `DiscardLRU` and `DiscardLFU`.
  * `predicate`: function that determines whether a file should be tracked/included in the cache. Currently only used for existing files when setting up the file cache. The default is to track every existing file.

!!! warn
    This is a potentially destructive operation since the file cache may delete files in the `root` directory to fit the given constraints.


Example usage:

```
# Create cache that keeps maximum 10 files and releases LRU objects
fc = NFileCache(root, 10, DiscardLRU())

# Add a new file:
path = add!(fc, key)
open(path, "w") do io
    write(path, filedata)
end

# Check to see if that file is there (and also increment its usage counters)
hit!(fc, key)

# Delete that file
delete!(fc, key)
```
