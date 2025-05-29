```
fit!(mach::Machine, rows=nothing, verbosity=1, force=false, composite=nothing)
```

マシン `mach` をフィットさせます。`mach` に `Node` 引数がある場合、まず `mach` が依存する他のすべてのマシンをトレーニングします。

他のマシンに触れずにマシンをフィットさせようとするには、`fit_only!` を使用します。オプションやフィッティングの内部ロジックについては、[`fit_only!`](@ref) を参照してください。
