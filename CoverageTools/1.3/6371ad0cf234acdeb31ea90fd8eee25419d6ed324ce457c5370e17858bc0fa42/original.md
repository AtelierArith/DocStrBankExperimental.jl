```
clean_folder(folder::AbstractString; include_memfiles::Bool=false)
```

Cleans up all the `.cov` and optionally `.mem` files in the given directory and subdirectories. Unlike `process_folder` this does not include a default value for the root folder, requiring the calling code to be more explicit about which files will be deleted.
