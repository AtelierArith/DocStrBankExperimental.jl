```
save(filename::AbstractString, f, args...; kwargs...)
save(io::IO, f, args...; kwargs...)
```

`modelproto(f, args...; kwargs...)` の結果を、パス `filename` のファイルまたは `io` にシリアライズします。

引数の説明については [`modelproto`](@ref) を参照してください。
