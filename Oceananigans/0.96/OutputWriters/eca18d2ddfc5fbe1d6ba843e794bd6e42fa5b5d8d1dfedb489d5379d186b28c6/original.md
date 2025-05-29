```
FileSizeLimit(size_limit [, path=""])
```

Return a schedule that actuates when the file at `path` exceeds the `size_limit`.

The `path` is automatically added and updated when `FileSizeLimit` is used with an output writer, and should not be provided manually.
