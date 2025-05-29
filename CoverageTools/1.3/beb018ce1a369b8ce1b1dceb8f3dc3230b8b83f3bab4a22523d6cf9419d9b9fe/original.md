```
clean_file(filename::AbstractString; include_memfiles::Bool=false)
```

Cleans up all `.cov` and optionally `.mem` files associated with a given source file. This only looks in the directory of the given file, i.e. the `.cov`/`.mem` files should be siblings of the source file.
