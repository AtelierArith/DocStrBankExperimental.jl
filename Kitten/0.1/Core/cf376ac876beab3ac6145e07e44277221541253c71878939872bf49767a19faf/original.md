```
dynamicfiles(folder::String, mountdir::String; headers::Vector{Pair{String,String}}=[], loadfile::Union{Function,Nothing}=nothing)
```

Mount all files inside the /static folder (or user defined mount point), but files are re-read on each request. The `headers` array will get applied to all mounted files
