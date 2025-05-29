```
diskusage(fp::AbstractPath)
```

Returns the total size in bytes of the `AbstractPath`.  This is guaranteed to give the same result as summing the `filesize` of all nodes in `walkpath(fp)` including directory node block sizes.

This is the preferred method for computing file or directory sizes for remote file systems as it should limit the number of remote calls where possible.
