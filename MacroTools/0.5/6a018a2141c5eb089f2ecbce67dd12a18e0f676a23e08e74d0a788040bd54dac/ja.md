```
inexpr(expr, x)
```

単純な式の一致; 式 `x` が `expr` 内に見つかる場合は `true` を返します。

```julia
inexpr(:(2+2), 2) == true
```
