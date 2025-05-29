```julia
download_jlcall(; ...) -> String
download_jlcall(filename::String; latest, force) -> String

```

Download or copy the `jlcall.m` MATLAB API function to the file `filename`.

By default, `jlcall.m` is copied into the current working directory from the `api` subfolder of the installed `MATDaemon.jl` source tree. The latest version of `jlcall.m` can instead be downloaded from GitHub by passing `latest = true`. The destination `filename` can be overwritten if it exists by passing `force = true`.
