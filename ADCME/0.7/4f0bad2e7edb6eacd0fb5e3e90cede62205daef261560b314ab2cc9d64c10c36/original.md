```
uncompress(zipfile::AbstractString, file::AbstractString)
```

Uncompress a zip file `zipfile` to `file` (a directory). Note this function does not check that the  uncompressed content has the name `file`. It is used as a hint to skip `uncompress` action.

Users may use `mv uncompress_file file` to enforce the consistency.
