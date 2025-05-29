```
NonRecursiveInterpreter <: Interpreter
```

`NonRecursiveInterpreter` は、解釈されるコード内の任意の `:call` 式を、Julia の通常のコード実行エンジンとネイティブコンパイラを使用して評価する [`Interpreter`](@ref) です。

`JuliaInterpreter.Compiled` は、後方互換性のために `NonRecursiveInterpreter` にエイリアスされています。
