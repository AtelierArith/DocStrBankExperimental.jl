```
CurlyExpr{FirstArg, E} <: AbstractExpr
```

`FirstArg`が`Symbol`である場合、`FirstArg{args...}`の形の式に一致します。それ以外の場合は、`args[1]{args[2:end]...}`に一致します。

## コンストラクタ

```
    CurlyExpr{FirstArg, E}(; args::Vector{E}) 
```
