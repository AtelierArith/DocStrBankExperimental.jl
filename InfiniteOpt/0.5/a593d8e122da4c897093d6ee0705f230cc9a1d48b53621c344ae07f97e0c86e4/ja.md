```
print_expression_tree(nlp::NLPExpr)
```

非線形式 `nlp` の木構造表現を印刷します。

**例**

```julia-repl
julia> expr = (x * sin(x)^3) / 2
(x * sin(x)^3) / 2

julia> print_expression_tree(expr)
/
├─ *
│  ├─ x
│  └─ ^
│     ├─ sin
│     │  └─ x
│     └─ 3
└─ 2
```
