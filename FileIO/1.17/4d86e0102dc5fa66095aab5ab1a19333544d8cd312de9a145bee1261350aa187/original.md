```
query(filename; checkfile=true)
```

Return a `File` object with information about the format inferred from the file's extension and/or magic bytes. If `filename` already exists, the file's magic bytes will take priority unless `checkfile` is false.
