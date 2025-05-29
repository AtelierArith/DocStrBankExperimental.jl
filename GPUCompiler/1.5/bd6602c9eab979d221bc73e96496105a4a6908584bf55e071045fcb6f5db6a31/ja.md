```
@device_code_native [io::IO=stdout, ...] ex
```

式 `ex` を評価し、コンパイルされた各 GPU カーネルの結果を `io` に [`GPUCompiler.code_native`](@ref) として出力します。他のサポートされているキーワードについては、[`GPUCompiler.code_native`](@ref) を参照してください。
