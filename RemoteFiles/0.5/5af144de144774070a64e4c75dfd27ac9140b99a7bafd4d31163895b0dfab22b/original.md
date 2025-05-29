```
load(rf::RemoteFile)
```

Load the contents of a remote file, downloading the file if it has not been done previously, reading the file from disk and trying to infer the format from filename and/or magic bytes in the file via [FileIO.jl](https://github.com/JuliaIO/FileIO.jl).
