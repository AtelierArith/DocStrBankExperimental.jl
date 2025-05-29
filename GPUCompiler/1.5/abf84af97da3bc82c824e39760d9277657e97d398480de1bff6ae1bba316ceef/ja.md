```
@device_code_llvm [io::IO=stdout, ...] ex
```

式 `ex` を評価し、コンパイルされた GPU カーネルごとに `io` に `InteractiveUtils.code_llvm` の結果を出力します。他のサポートされているキーワードについては、[`GPUCompiler.code_llvm`](@ref) を参照してください。

関連情報: InteractiveUtils.@code_llvm
