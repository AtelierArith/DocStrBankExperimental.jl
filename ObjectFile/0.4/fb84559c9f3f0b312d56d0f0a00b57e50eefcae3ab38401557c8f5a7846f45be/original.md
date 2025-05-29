```
path(oh::ObjectHandle)
```

Return the absolute path to the given `ObjectHandle`, if it was a file loaded from the local disk.  If it was loaded from a general `IOStream` or in some other way such that the path is unknown or unknowable, return the empty string.
