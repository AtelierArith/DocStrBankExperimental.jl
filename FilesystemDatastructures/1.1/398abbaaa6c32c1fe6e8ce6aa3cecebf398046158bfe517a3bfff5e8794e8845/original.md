```
rebuild!(fc::FileCache; predicate::Function = x -> true)
```

Rebuilds the file cache datastructures within memory from disk.  This is not a lossless operation; last access times may be inaccurate and number of times accessed will be set to 1 for any key that was not previously tracked.  This is done automatically when creating a new cache; the file cache will scan its root directory and populate itself with the values gathered using this function.

The `predicate` keyword can be used to pass a predicate function (input: `key`, output: `Bool`) to filter which files in the root directory that should be tracked/included in the cache. The default is to include every file.
