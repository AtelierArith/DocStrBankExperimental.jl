```
SizeConstrainedFileCache <: FileCache
```

Represents a size-constrained file cache.  Configurable with different policies for when to discard elements from the cache and how to choose which elements to discard.

```
SizeConstrainedFileCache(root, target_func, discard_func; predicate=x->true)
```

Construct a new file cache. Arguments:

  * `root`: the root directory of the cache.
  * `target_func`: function that return the (maximum) number of bytes that files in the cache may occupy, see e.g. `TargetSizeKeepFree` and `TargetSizeConstant`.
  * `discard_func`: function that return the eviction order, see e.g. `DiscardLRU` and `DiscardLFU`.
  * `predicate`: function that determines whether a file should be tracked/included in the cache. Currently only used for existing files when setting up the file cache. The default is to track every existing file.

!!! warn
    This is a potentially destructive operation since the file cache may delete files in the `root` directory to fit the given constraints.


Example usage:

```
# Create cache that keeps 10GB free and releases LRU objects
scfc = SizeConstrainedFileCache(root, TargetSizeKeepFree(10*1024^3), DiscardLRU())

# Add a new file:
path = add!(scfc, key, filesize)
open(path, "w") do io
    write(path, filedata)
end

# Check to see if that file is there (and also increment its usage counters)
hit!(scfc, key)

# Delete that file
delete!(scfc, key)
```
