```
MacroCall(; name::Union{Symbol, Expr, GlobalRef}, line::Union{LineNumberNode, NotProvided} = not_provided, args::Vector{Any} = [])
```

マクロ呼び出し式に一致します。`MacroCall`オブジェクトは、1つ以上の式に適用でき、別の`MacroCall`を生成します。
