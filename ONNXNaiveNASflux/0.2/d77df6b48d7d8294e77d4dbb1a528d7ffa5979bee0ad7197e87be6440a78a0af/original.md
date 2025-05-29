```
save(filename::AbstractString, mp::ONNX.ModelProto)
save(io::IO, mp::ONNX.ModelProto)
```

Serialize the given [`ONNX.ModelProto`](@ref) to a file with path `filename` or to `io`.
