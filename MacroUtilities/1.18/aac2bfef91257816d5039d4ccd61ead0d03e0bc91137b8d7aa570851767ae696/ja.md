```
AssignExpr{L,R}(; lhs::L, rhs::R, allow_kw)
```

`lhs = rhs` の代入式に一致します。

`allow_key == true` の場合、ヘッドが `:kw` の代入式にも一致します。
