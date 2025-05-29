```
@dynamicfiles(folder::String, mountdir::String, headers::Vector{Pair{String,String}}=[])
```

Mount all files inside the /static folder (or user defined mount point), but files are re-read on each request
