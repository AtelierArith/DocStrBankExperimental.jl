```
require_file(f::Function, file::Union{String, Array{String}})
```

If any of the files/links/directories in `file` does not exist, execute `f`.
