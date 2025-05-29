```
AssignExpr{L,R}(; lhs::L, rhs::R, allow_kw)
```

Matches a `lhs = rhs` assignment expression. 

If `allow_key == true`, also matches an assignment expression with head `:kw`
