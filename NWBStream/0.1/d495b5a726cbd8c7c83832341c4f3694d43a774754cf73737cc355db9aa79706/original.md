```
cachefs(protocol::String="http") -> CachingFileSystem
```

Create a caching file system object using `fsspec_cached.CachingFileSystem`. The `protocol` argument sets the underlying file system protocol to be used and is set to `"http"` by default.

Returns a new `CachingFileSystem` object that can be used for reading and writing files from the specified file system.
