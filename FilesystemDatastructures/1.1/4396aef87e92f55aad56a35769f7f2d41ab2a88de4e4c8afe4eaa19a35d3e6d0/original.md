```
get_disk_freespace(path)
```

Returns the amount of available disk space within the filesystem that contains the given path.  Internally uses `statfs()` which is only implemented on Linux and macOS; throws an error on all other systems.
