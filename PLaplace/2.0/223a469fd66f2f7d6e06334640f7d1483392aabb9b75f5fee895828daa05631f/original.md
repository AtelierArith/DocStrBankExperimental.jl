```
write_statistics_header(filename::String; guarded::Bool=false)
```

Clears and writes a header for a statistics log to the given file. In case the file does not exist, it will be created, but only if the path exists. If guarded checks before if file already contains a header and then does not overwrite potentially previous results.
