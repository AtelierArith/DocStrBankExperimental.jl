```
RecursiveInterpreter <: Interpreter
```

`RecursiveInterpreter` は、解釈されているコード内のすべての `:call` 式を再帰的に解釈する [`Interpreter`](@ref) です。

このインタープリタを使用すると、コードは完全に解釈されたモードで実行されます。実行のためにコンパイルされることは決してありません。
