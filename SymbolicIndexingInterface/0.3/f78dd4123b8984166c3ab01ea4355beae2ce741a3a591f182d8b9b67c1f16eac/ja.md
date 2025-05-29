```
symbolic_type(x) = symbolic_type(typeof(x))
symbolic_type(::Type)
```

型のシンボリックタイプ特性を取得します。`Symbol`および`Expr`を除くすべての型については、デフォルトで[`NotSymbolic`](@ref)になります。両者は[`ScalarSymbolic`](@ref)です。

関連情報: [`ScalarSymbolic`](@ref), [`ArraySymbolic`](@ref), [`NotSymbolic`](@ref)
