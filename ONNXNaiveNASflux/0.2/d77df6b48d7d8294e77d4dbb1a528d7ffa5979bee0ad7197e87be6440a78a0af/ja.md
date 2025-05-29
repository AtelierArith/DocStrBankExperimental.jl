```
save(filename::AbstractString, mp::ONNX.ModelProto)
save(io::IO, mp::ONNX.ModelProto)
```

与えられた [`ONNX.ModelProto`](@ref) をファイルパス `filename` にシリアライズするか、`io` にシリアライズします。
