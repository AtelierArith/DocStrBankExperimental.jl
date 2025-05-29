```
OtelLogTransformer(resource::Resource)
```

これは、[`TransformerLogger`](https://github.com/JuliaLogging/LoggingExtras.jl#transformerlogger-transformer)に対して関数 `f` として使用できます。このトランスフォーマーを適用した後、[`LogRecord`](@ref) が返されます。
