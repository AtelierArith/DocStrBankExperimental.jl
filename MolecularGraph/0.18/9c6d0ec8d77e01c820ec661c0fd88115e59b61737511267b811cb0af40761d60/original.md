```
sdfilescanner(file::IO)
sdfilescanner(path::AbstractString)
```

Read SDFile data from input stream (or a file path as a string) and return a lazy iterator that yields metadata.
