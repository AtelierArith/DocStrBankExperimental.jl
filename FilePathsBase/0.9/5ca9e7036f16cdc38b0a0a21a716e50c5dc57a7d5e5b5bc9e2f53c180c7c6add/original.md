```
download(url::Union{AbstractString, AbstractPath}, localfile::AbstractPath)
```

Download a file from the remote `url` and save it to the `localfile` path.

NOTE: Not downloading into a `localfile` directory matches the base Julia behaviour. https://github.com/rofinn/FilePathsBase.jl/issues/48
