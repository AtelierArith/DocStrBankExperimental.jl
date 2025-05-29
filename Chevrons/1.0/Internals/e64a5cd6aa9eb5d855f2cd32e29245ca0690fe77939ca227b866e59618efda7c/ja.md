```
enable_repl(on::Bool=true)
```

REPL統合を有効または無効にします。

有効にすると、REPL内のすべてのコマンドは[`chevrons`](@ref)によって変換されます。

これを`startup.jl`ファイル内で呼び出すことができます。
